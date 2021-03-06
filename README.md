# Introduction
ACL unit test environment for SONiC

# Getting Started
## Install requirment tools
```
sudo apt update

# sswss-common
sudo apt-get install -y make libtool m4 autoconf dh-exec debhelper cmake pkg-config \
                        libhiredis-dev libnl-3-dev libnl-genl-3-dev libnl-route-3-dev swig3.0 \
                        libpython-dev g++ python python-dev

# googletest
mkdir -p /tmp/gtest && cd /tmp/gtest
git clone https://github.com/google/googletest.git
cd googletest && cmake . && make && sudo make install

# SAI
sudo apt install -y doxygen graphviz aspell

# sonic-swss
sudo apt-get install -y libhiredis0.13

# install perl  module
sudo perl -MCPAN -e "install XML::Simple"
## If meet some problemes, you can try to install by apt-get
## sudo apt install -y libxml-simple-perl
```

## Starting redis-server and open UNIX socket
```
sudo apt install -y redis-server
sudo mkdir -p /var/run/redis/
echo "unixsocket /var/run/redis/redis.sock" | sudo tee --append  /etc/redis/redis.conf
echo "unixsocketperm 777" | sudo tee --append  /etc/redis/redis.conf
sudo service redis-server restart
```

## Build the test environment
```
git clone --recurse-submodules https://github.com/ezio-chen/sonic-swss-acl-dev.git
cd sonic-swss-acl-dev

# Create build environment and build
mkdir -p <build dir> && cd <build_dir>
sh <source_dir>/build.sh
make
```
