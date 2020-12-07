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

# Installation de Docker & Docker compose

suivre les intructions suivantes (**seulement pour ubuntu**)

```
sudo apt update
sudo apt install docker.io containerd docker-compose
systemctl start docker
systemctl enable docker

systemctl status docker

```

# Installation de GitLab:
## Préparation

```
mkdir -p gitab;cd gitlab/

vim .env

GITLAB_HOME=/srv/gitlab
vim docker-compose.yml


```

Ajout dans le fichier **docker-compose.yml** comme suivant:

```

mage: 'gitlab/gitlab-ce:latest'
  restart: always
  hostname: 'gitlab.hakase-labs.io'

  environment:
    GITLAB_OMNIBUS_CONFIG: |
      # Add any other gitlab.rb configuration here, each on its own line
      external_url 'https://gitlab.hakase-labs.io'
      gitlab_rails['gitlab_shell_ssh_port'] = 2224
      nginx['redirect_http_to_https'] = true
      nginx['ssl_certificate'] = "/etc/gitlab/ssl/fullchain.pem"
      nginx['ssl_certificate_key'] = "/etc/gitlab/ssl/privkey.pem"
      nginx['ssl_dhparam'] = "/etc/gitlab/ssl/dhparams.pem"  

  ports:
    - '80:80'
    - '443:443'
    - '2224:22'

  volumes:
    - '${GITLAB_HOME}/config:/etc/gitlab'
    - '${GITLAB_HOME}/logs:/var/log/gitlab'
    - '${GITLAB_HOME}/data:/var/opt/gitlab'
    - '${GITLAB_HOME}/config/ssl:/etc/gitlab/ssl`

```

## Generer SSL certificat

```
sudo apt install certbot
certbot certonly --rsa-key-size 2048 --standalone --agree-tos --no-eff-email --email user@hakase-labs.io -d gitlab.hakase-labs.io
```
