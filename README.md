#!/bin/sh

echo -e "\033[0;32m[.sshd]\033[0m"

pacman -S --noconfirm --needed openssh

if ! systemctl is-enabled sshd; then
    systemctl enable sshd
fi

if ! systemctl is-active sshd; then
    systemctl start sshd
fi

echo -e "\033[0;32m[.sshd] : success\033[0m"
