## bacula-client docker image based on alpine linux

## Synopsis

Very small footprint bacula-client docker image can be used to back up local
storage on docker nodes like CoreOS etc.

## Installation and usage

Either pull the image directly from Docker Hub:
```
docker run -d --restart=always --name bacula-fd \
        -p 9102:9102 \
        -v /:/mnt:ro \
        -e FD_PASSWORD='bacula-fd password' \
        -e FD_NAME=$(hostname) \
        martmaiste/bacula-fd
```

Or build it locally:
```
git clone https://github.com/martmaiste/bacula-fd.git
docker build -t bacula-fd bacula-fd
```

Run the container:
```
docker run -d --restart=always --name bacula-fd \
	-p 9102:9102 \
	-v /:/mnt:ro \
	-e FD_PASSWORD='bacula-fd password' \
	-e FD_NAME=$(hostname) \
	bacula-fd
```

## Credits

[Bacula (open source) containers for Docker by RedCoolBeans](https://github.com/RedCoolBeans/docker-bacula-opensource)
