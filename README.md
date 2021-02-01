Run i3 from container to x server host
docker build -t ubuntu-i3 . -f ubuntu-systemd-vim-i3
docker run -d --name ubuntu-i3 --privileged -v /tmp/.X11-unix:/tmp/.X11-unix:ro -v /sys/fs/cgroup:/sys/fs/cgroup:ro ubuntu-i3
