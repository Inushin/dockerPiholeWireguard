# 🐳 Docker + PiHole + WireGuard 🐳

![piholeWireguard](https://user-images.githubusercontent.com/57062736/205506991-0758a87f-c009-4dac-bc47-927ab710cc2a.png)

If you find this useful, remember about giving a start ⭐ to this repo or share it 🔁

## Description 📋

![docker_facebook_share](https://user-images.githubusercontent.com/57062736/139103227-36f3cb32-c3c1-4158-b99e-25a31e955f44.png)

This is a complete stack for running PiHole for AdBlock and WireGuard as VPN, with Docker.

It is composed by 2 containers:

- `pihole`, blocking ads.
- `wireguard`, personal and free VPN for our server.

## Installation ⌨

![Docker Installation Illustration](https://user-images.githubusercontent.com/57062736/139102730-d6f51d53-ffb3-44bb-be5e-2bdf48d91295.png)

0. You need **Docker** and **Docker Compose** where you are going to launch this so, if you do not have it... click [HERE](https://github.com/Inushin/dockerPiholeWireguard#installing-docker-and-docker-compose-) or go to the end of this `.md` ^^

1. Clone this rep.

2. Edit `wireguard.env` and `pihole.env` with the information you want.

3. Run `docker compose up` 😀.

4. For having our PiHole database updated, run the script `updatePihole` with crontab (set the crontab with the root user). This script will remove and deploy again our PiHole container pulling a new and updated image.

5. Check that the 2 containers are deployed:

```yaml
pihole              "/s6-init"          pihole              running (healthy)   53/tcp, 53/udp, 67/tcp, 80/tcp, 443/tcp, 67/udp
wireguard           "/init"             wireguard           running             0.0.0.0:51820->51820/udp, :::51820->51820/udp
```

## Docker's useful commands 📑
![Docker Commands Illustration](https://user-images.githubusercontent.com/57062736/139102966-25f28be1-f768-49bd-a8a1-915a8465de9e.png)

- Run Docker Compose: `docker compose up -d` / `docker compose up`

- Check Docker Compose's volumens status: `docker compose ps -a` / `docker compose ps`

- Check Docker's images: `docker images -a`

- Remove Docker's images: `docker rmi -f imageID1 imageID2 ...` (-f = force)

- Enter to a Docker's volumen: `docker compose exec VolumenID sh` / `docker compose exec VolumenID bash`

- Copy a file to the docker we want to: `docker cp file docker_id:/dir`

- Remove all dangling (not tagged or associated with a container) containers, volumes, networks and images: `docker system prune`

- Remove all unused containers and images with at least one container associated to them: `docker system prune -a`

- Shows all unused local images: `docker images ls -f dangling=true`

- Shows all unused local volumes: `docker volume ls -f dangling=true`

- Remove all local volumes not used by at least one container: `docker volume prune`

## Installing Docker and Docker Compose 🛠
![Docker Composer](https://user-images.githubusercontent.com/57062736/141182130-b8ed2d7a-9a68-4387-b838-ba0d44bb4e0e.png)

**Adjust the installation to your OS. Here you have the one for a VPS with Debian 11**

- Docker and Docker Compose installation

1. Update the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:

```yaml
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

2. Add Docker’s official GPG key:

```yaml
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3. Use the following command to set up the repository:

```yaml
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```


4. Starts Docker's service each time you run the SO: `chkconfig docker on`

```yaml
sudo apt-get update
```

5. Install Docker Engine, containerd, and Docker Compose. This will install the latest version:

```yaml
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

6. Give permissions to the desired user by adding it the  `docker` group:

```yaml
usermod -aG docker $USER
```

7. Check the version and the installation: `docker compose version` `docker --version`

## ⭐ Feedback and bugs 🐞

If you find any bug or just want to give your feedback (remember the ⭐ ^^), **Feel free to do it**. I am, like you, constantly learning and things change so quickly that... no one knows ^^

## Version control 📝

- [v1.0 - Current](https://github.com/Inushin/dockerPiholeWireguard/-/tree/v1.0) - Creation of the rep with the config finished - 05/12/2022
