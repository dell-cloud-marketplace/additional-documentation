# nsenter
[nsenter](https://github.com/jpetazzo/nsenter) is a utility which lets you enter into a Docker container from the host.

First, on the Docker host, create file **install.sh** with the following contents:

```no-highlight
apt-get install -y build-essential
curl https://www.kernel.org/pub/linux/utils/util-linux/v2.24/util-linux-2.24.tar.gz \
| tar -zxf-
cd util-linux-2.24
./configure --without-ncurses
make nsenter
cp nsenter /usr/local/bin
```

Next, do:

```no-highlight
chmod +x install.sh
sudo ./install.sh
```

Find the id of your container via ```sudo docker ps```. The output (truncated to the left of the screen), should look something like this:

```no-highlight
CONTAINER ID        IMAGE               COMMAND 
49ad89e9cc57        dell/<image name>   "/run.sh"      
```

Assuming, for example, a container ID of **49ad89e9cc57**, please do:

```no-highlight
PID=$(sudo docker inspect --format '{{.State.Pid}}' 49ad89e9cc57); \
sudo nsenter --target $PID --mount --uts --ipc --net --pid
```

You should now be in the container, as root.
