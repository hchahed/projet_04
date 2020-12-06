# Projet_04
# OpenClassRooms Projet 04
# Dans CENTOS

## Installation de Git dans CENTOS 8
```bash
sudo dnf update -y
sudo dnf install git -y
```

## Installation de Gitlab dans Centos 8

```bash
sudo dnf -y install curl policycoreutils openssh-server openssh-clients postfix
systemctl start sshd 
systemctl start postfix
systemctl enable sshd
systemctl enable postfix
curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | sudo bash
sudo dnf repolist
sudo dnf install gitlab-ce -y


```

Dans le cas d'une erreur d'installation on utilisera la commande ci-dessous:

```bash
dnf package clean

```
# DANS UBUNTU:






## Installation de Pelican:
1. d'abord installer python3 et pip
```bash
sudo add-apt-repository universe
sudo apt install python3-pip

```
# Utilisation de Pelican

## Creation d'un article

Dans un fichier **.md** faire comme suivant:

```
Title: Hello World From OpenClassRooms to Hichem
Date: 2020-12-06 22:00
Category: Review
Authors Hichem CHAHED


Summary: Premiere introduction à l'outil de génération de HTML


Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.


```
