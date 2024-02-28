## docker engine install

### in ubuntu or debian, just run `apt install docker.io`

OR

### ubuntu version download from [dists](https://download.docker.com/linux/ubuntu/dists/)

1. `lsb_release -a`, check ubuntu code name,
2. select codename/pool/stable/amd64/ or /other-versions
3. download all updated deb version, then `dpkg -i ***.deb`
4. order: `containerd`, `cli`, `ce`, `rootless`, `compose` and `scan`.

### permission

1. sudo groupadd docker
2. sudo usermod -aG docker $USER
3. newgrp docker
4. docker run hello-world
5. reboot
