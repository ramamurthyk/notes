# Docker Setup on Linux

Install docker from the snap store

By default, Docker is only accessible with root privileges (sudo). If you want to use docker as a regular user, you need to add your user to the docker group.

```bash
sudo addgroup --system docker
sudo adduser $USER docker
newgrp docker
sudo snap disable docker
sudo snap enable docker
```

Warning: if you add your user to the docker group, it will have similar power as the root user. For details on how this impacts security in your system, see: [https://docs.docker.com/engine/security/#docker-daemon-attack-surface](https://docs.docker.com/engine/security/#docker-daemon-attack-surface)

Start on boot

```bash
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```