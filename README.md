# Projet_04
# OpenClassRooms Projet 04

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
