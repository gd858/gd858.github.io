---
title: Setting up Next Cloud ...


---

Hopefully this takes 5 minutes. I just want a place to temporarily store files on my network. This computer has the jellyfin server so it's calm. 


set up docker: 
```bash
sudo dnf -y install dnf-plugins-core
sudo dnf-3 config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo


sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo systemctl start docker

sudo systemctl status docker
```
https://github.com/nextcloud/all-in-one#nextcloud-all-in-one
o
To setup NExt Cloud
```bash
# For Linux and without a web server or reverse proxy (like Apache, Nginx, Caddy, Cloudflare Tunnel and else) already in place:
sudo docker run \
--init \
--sig-proxy=false \
--name nextcloud-aio-mastercontainer \
--restart always \
--publish 80:80 \
--publish 8080:8080 \
--publish 8443:8443 \
--volume nextcloud_aio_mastercontainer:/mnt/docker-aio-config \
--volume /var/run/docker.sock:/var/run/docker.sock:ro \
nextcloud/all-in-one:latest
```
result
```bash
Initial startup of Nextcloud All-in-One complete!
You should be able to open the Nextcloud AIO Interface now on port 8080 of this server!
E.g. https://internal.ip.of.this.server:8080
⚠️ Important: do always use an ip-address if you access this port and not a domain as HSTS might block access to it later!

If your server has port 80 and 8443 open and you point a domain to your server, you can get a valid certificate automatically by opening the Nextcloud AIO Interface via:
https://your-domain-that-points-to-this-server.tld:8443
[27-Oct-2024 23:53:06] NOTICE: fpm is running, pid 150
[27-Oct-2024 23:53:06] NOTICE: ready to handle connections
[Sun Oct 27 23:53:06.616652 2024] [mpm_event:notice] [pid 145:tid 145] AH00489: Apache/2.4.62 (Unix) OpenSSL/3.3.2 configured -- resuming normal operations
[Sun Oct 27 23:53:06.617167 2024] [core:notice] [pid 145:tid 145] AH00094: Command line: 'httpd -D FOREGROUND'
{"level":"info","ts":1730073186.6288419,"msg":"using config from file","file":"/Caddyfile"}
{"level":"info","ts":1730073186.6314757,"msg":"adapted config to JSON","adapter":"caddyfile"}

```
