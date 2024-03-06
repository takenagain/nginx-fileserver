# docker-share-files

![Docker Image CI](https://github.com/rodolfobandeira/docker-share-files/workflows/Docker%20Image%20CI/badge.svg)

## Description

This Docker repository starts an HTTP server on port 8080 (<http://localhost:8080>) showing the famous "index of" listing all files from the local folder `./shared-files`. It is a great way to quickly share files through the network. You can get your private IP with `ifconfig`(MacOS/Linux/*BSD) or`ipconfig`(Windows).

### How it works

We have two folders under this project:

- [shared-folder](./shared-folder) - files to be shared
- [config](./config) - Nginx configuration

#### shared-folder

- Just add any file here and when you start your docker, they will be listed to anyone download it  
- If you add an `index.html` your "index of" feature will be gone.

#### config

- Here we have our Nginx `default.conf` file. Wherever you change here, will be reflected inside your docker. Keep in mind that you will need to restart Nginx or the docker container if you change the nginx config.

- `./config/default.conf` points to `/etc/nginx/conf.d/default.conf`. The same way, `./shared-folder` points to (Docker) `/usr/share/nginx/html` folder.

### Quickstart

1) `git clone https://github.com/takenagain/nginx-fileserver.git`

2) `docker compose up --build`

Open your browser and try the address: `http://localhost:8080`. You should see something like this:

![index of](config/img.png)

---
