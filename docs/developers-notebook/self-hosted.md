# Self-Hosted Works

## Self-Host SSH Server

- OpenSSH: <https://www.openssh.com/>

```dockerfile
FROM ubuntu:latest

RUN apt update && apt install  openssh-server sudo -y

RUN useradd -rm -d /home/ubuntu -s /bin/bash -g root -G sudo -u 1000 test 

RUN  echo 'test:test' | chpasswd

RUN service ssh start

EXPOSE 22

CMD ["/usr/sbin/sshd","-D"]
```

```bash
docker build -t "my-ssh-server" --file "./ssh-server.dockerfile" .
docker run --rm --publish 22:22 my-ssh-server
```

## Self-Host VPN Server

### OpenVPN

### Wireguard

```yml
version: "2.1"
services:
  wireguard:
    image: lscr.io/linuxserver/wireguard:latest
    container_name: wireguard
    cap_add:
      - NET_ADMIN
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
      - SERVERURL=auto #optional
      - SERVERPORT=51820 #optional
      - PEERS=1 #optional
      - PEERDNS=auto #optional
      - INTERNAL_SUBNET=10.13.13.0 #optional
      - ALLOWEDIPS=0.0.0.0/0 #optional
      - PERSISTENTKEEPALIVE_PEERS= #optional
      - LOG_CONFS=true #optional
    volumes:
      - /Users/giraycoskun/Documents/Projects/SelfHosted/config:/config
    ports:
      - 51820:51820/udp
    sysctls:
      - net.ipv4.conf.all.src_valid_mark=1
    restart: unless-stopped
```

```bash
docker-compose up
```

## Self-Host Reverse Proxy Server for LocalHost

### localtonet

- <https://localtonet.com/>

???+ warning

    It's not OSS, but i has free tier.

I think one of the best options out there. Very easy to use and set up. And it supports UDP with a free account.

No idea about the security of it though.

- **Download**: <https://localtonet.com/download>

## Self-Hosted Ubuntu Terminal

```bash
docker pull ubuntu:latest
docker run -it --rm -d --publish 22:22  ubuntu:latest /sbin/init
```

## Awesome Lists

- <https://github.com/anderspitman/awesome-tunneling>
- <https://github.com/awesome-selfhosted/awesome-selfhosted>
