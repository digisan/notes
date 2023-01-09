## docker engine install

ubuntu version download from [dists](https://download.docker.com/linux/ubuntu/dists/)

1. `lsb_release -a`, check ubuntu code name,
2. select codename/pool/stable/amd64/ or /other-versions
3. download all updated deb version, then `dpkg -i docker*.deb` and `dpkg -i containerd*.deb`