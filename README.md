# Dockerized Posbox

Docker PosBox image for posbox-less deployment.

This image is prepared for [AwesomeFoodCoops](https://github.com/AwesomeFoodCoops/odoo-production) PoS

## Infrastructure

![](https://raw.githubusercontent.com/AwesomeFoodCoops/docker-posbox/master/readme/posboxless_setup.png)

If you are running your Point of Sale on a Debian-based Linux distribution,
you do not need the POSBox as you can run its software locally.

For this purpose, you can use this dockerized version.

## Install

This will update packages, install docker, and install the docker-posbox
in `/posbox/docker-posbox`

```
curl -fsSL https://raw.githubusercontent.com/AwesomeFoodCoops/docker-posbox/master/install.sh -o install-posbox.sh && sh install-posbox.sh

```

### Manual Install (Advanced)

1. Clone this repository `git clone https://github.com/AwesomeFoodCoops/docker-posbox` && `cd docker-posbox`

2. Edit the `odoo.conf` according to your requirements.

3. Run
```
$ docker-compose build --pull
$ docker-compose up -d
```

4. Try to access: `http://localhost:8069/hw_proxy/status`.

### Upgrading to new versions

```
$ cd /posbox/docker-posbox
$ docker-compose down
$ docker-compose build --pull
$ docker-compose up -d
```

## Usage

`docker-compose` commands must be ran on the `/posbox/docker-posbox` path,
where the `docker-compose.yml` file is located.

### Checking logs


Last 100 lines:

```
$ docker-compose --tail 100
```

Live logs:

```
$ docker-compose --tail 100 -f
```

### Custom odoo.conf

It's possible to edit the `odoo.conf` file.

This file is copied into the container when running `docker-compose build`.

### Restarting posbox container

```
$ docker-compose down
$ docker-compose up -d
```

## Known Issues

- Mozilla Firefox gives MixedContent error, but Google Chrome works fine out of the box.
It might be possible to use Firefox, with some configuration.

## Contributors

* Iván Todorovich (https://www.druidoo.io)

## Maintainer

<img src="https://www.druidoo.io/web/image/1136/druidoo14-09.png" 
alt="Druidoo" width="200"/>

This repository is maintained by Druidoo.

