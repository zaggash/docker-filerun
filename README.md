Based on linuxserver.io baseimage but NOT SUPPORTED by them.

# zaggash/docker-filerun
[![](https://images.microbadger.com/badges/image/zaggash/docker-filerun.svg)](https://microbadger.com/images/zaggash/docker-filerun "Get your own image badge on microbadger.com")
[hub]: https://hub.docker.com/r/zaggash/docker-filerun/

FileRun File Manager: access your files anywhere through self-hosted secure cloud storage, file backup and sharing for your photos, videos, files and more. [Filerun](http://www.filerun.com/)

![filerun](https://www.filerun.com/images/long-logo.png)

## Usage

```
docker create --name=filerun \
-v <path to data>:/config \
-e TZ \
-e PGID=<gid> -e PUID=<uid> \
-p 80:80 \
zaggash/docker-filerun
```

**Parameters**

* `-p 80` - the port(s)
* `-v /config` - where it should store config files and logs
* `-e PGID` for GroupID - see below for explanation
* `-e PUID` for UserID - see below for explanation
* `-e TZ` for timezone information

It is based on alpine linux with s6 overlay, for shell access whilst the container is running do `docker exec -it filerun /bin/bash`.

### User / Group Identifiers

Sometimes when using data volumes (`-v` flags) permissions issues can arise between the host OS and the container. We avoid this issue by allowing you to specify the user `PUID` and group `PGID`. Ensure the data volume directory on the host is owned by the same user you specify and it will "just work" ™.

## Setting up the application 

Webui is on port 80


## Info

* To monitor the logs of the container in realtime `docker logs -f filerun`.
