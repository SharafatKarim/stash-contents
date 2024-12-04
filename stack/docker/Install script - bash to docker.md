---
Owner: Sharafat Karim
Last edited time: 2022-12-12T10:36
---
This script is from our Redwan bro,

```Bash
docker_setup() {
    sudo pacman -S --noconfirm --needed docker docker-compose ctop dbeaver
    sudo systemctl start docker.service
    sudo systemctl enable docker.service
    sudo usermod -aG docker "$USER"
}

docker_setup
```