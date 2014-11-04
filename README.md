# OpenBR SDK
The goal of this project is to create a development environment to use & code with [OpenBR](http://openbiometrics.org) and [OpenCV](http://opencv.org)

# Install
First, you'll have to install [docker](https://docs.docker.com/installation/#installation).

Then, install [node.js](http://nodejs.org/).

At last, install [docker-cmd](https://github.com/iorga-group/docker-cmd#installation).

Now, you can clone this project, go inside it and build the OpenBR SDK docker image:

```bash
git clone https://github.com/anthony-o/openbr_sdk.git
cd openbr_sdk
sudo docker-cm build anthony_o/openbr_sdk
```

# Use
Just before creating or using an OpenBR SDK container, execute this (thanks to [stackoverflow](http://stackoverflow.com/a/25280523/535203)):

```bash
xauth nlist :0 | sed -e 's/^..../ffff/' | sudo xauth -f /tmp/.docker.xauth nmerge -
```

To create a new OpenBR SDK container, do:

```bash
sudo docker-cm run openbr_sdk
```

If the container is already created but not running do:

```bash
sudo docker start openbr_sdk && sudo docker attach openbr_sdk
```

If the container is already created and running do:

```bash
sudo docker attach openbr_sdk
```

With that container running, you'll have by default `/tmp` shared with the docker host in order to exchange some images for example.
