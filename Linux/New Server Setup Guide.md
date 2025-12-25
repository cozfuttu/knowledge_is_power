
## Initial Setup

#### Update, Upgrate, Reboot

```sh
sudo apt update && sudo apt -y upgrade
sudo reboot
```

#### Create a sudo user (non-root)

```sh
sudo adduser can
sudo usermod -aG sudo can
```

```sh
# From your local machine (NOT the server):
ssh-copy-id can@YOUR_SERVER_IP
```

#### Harden SSH

```sh
sudo nano /etc/ssh/sshd_config
```

Recommended changes:

```
Port 22              # (Optional) change to a non-default like 2222
PermitRootLogin yes  # you might want no
PasswordAuthentication no
PubkeyAuthentication yes
# Limit who can SSH in (optional, but good)
AllowUsers can
```

Apply changes and allow the port in firewall if you change it:

```sh
sudo systemctl reload ssh
```

#### Basic Firewall (UFW)

```sh
sudo apt -y install ufw
# If you changed the SSH port, use that here instead of 22
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status
```

#### Useful Base Packages

```sh
sudo apt -y install build-essential curl wget git unzip htop net-tools ca-certificates gnupg lsb-release software-properties-common
```

#### Automatic security updates

```sh
sudo apt -y install unattended-upgrades
sudo dpkg-reconfigure -plow unattended-upgrades
```

## Node

#### NVM

###### Installation

Reference: https://github.com/nvm-sh/nvm#installing-and-updating

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
# Logout - Login
nvm install --lts
node -v && npm -v # v22.21.0
```

#### PM2

###### Installation

```sh
npm i -g pm2
pm2 startup systemd
# Follow the printed command, then:
pm2 save
```

###### Example Service Start

```sh
# In app folder:
pm2 start "npm start" --name myapp
pm2 save
```

#### Package Managers

```sh
npm i -g corepack@latest yarn
corepack enable pnpm
```


## Docker

#### Installation

###### Uninstall Old Versions

Reference: https://docs.docker.com/engine/install/ubuntu/#uninstall-old-versions

```sh
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

###### Installing using `apt`

Reference: https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

```sh
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

###### Verify Docker is running

```sh
sudo systemctl status docker
```

###### Add user to docker group

```sh
sudo usermod -a -G docker $USER
logout
```

###### Verify Installation

```sh
docker run hello-world
```


#### Postgresql

###### Install PostgreSQL tools (psql command)

```sh
sudo apt -y install postgresql-client
```

###### Run PostgreSQL

```sh
docker run --name postgres -e POSTGRES_PASSWORD=password -p 5432:5432 -d postgres
```

###### Make PostgreSQL Start Automatically After a Reboot

```sh
docker update --restart always postgres
```

###### Backup single database

```sh
docker exec -t postgres pg_dump -U postgres -F c <db_name> > backup.sql
```
###### Backup all databases

```sh
docker exec -t postgres pg_dumpall -U postgres > backup.sql
```

###### Restore Database (if used pg_dump, NOT pg_dumpall)

```sh
docker exec -i postgres pg_restore -U postgres < backup.sql
```

###### Restore Database (if used pg_dumpall, NOT pg_dump)

```sh
docker exec -i postgres psql -U postgres < backup.sql
```

If doesn't work:

```sh
cat backup.sql | docker exec -i postgres psql -U postgres
```

!Note: when you restore databases, your postgres user password might also change, to update it, run:

```sh
docker exec -it postgres psql -U postgres
ALTER USER postgres WITH PASSWORD 'newpassword';
```

#### Redis

⚠️ **Important Note**: If you have a docker app which uses redis, you need to connect it using:
`redis://<docker_bridge_network_ipaddr>:6379`

you need to create a docker network for this.
###### Running

```sh
docker run --name redis --network redis_network -i -t -p 6379:6379 redis redis-server --save 60 1 --requirepass "password"
```

to get the `<docker_bridge_network_ipaddr>`, run the following command:

```
docker inspect redis | grep -A 20 "Networks"
```
and get the `IPAddress` value.

## Nginx

#### Installation

```sh
sudo apt -y install nginx
sudo systemctl enable --now nginx
```

#### Let’s Encrypt (HTTPS)

```sh
sudo snap install core && sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

###### Create an Example Nginx Server Block

```sh
sudo tee /etc/nginx/sites-available/example.com >/dev/null <<'EOF'
server {
    listen 80;
    listen [::]:80;
    server_name example.com www.example.com;

    root /var/www/example.com;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
EOF

sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl reload nginx
sudo certbot --nginx -d example.com -d www.example.com
# Auto-renew test:
sudo certbot renew --dry-run
```

## Other

#### Chromium

###### Install Chromium

```sh
sudo apt -y install chromium
```

###### Install Chromium Dependencies For Linux

Reference: https://pptr.dev/troubleshooting#chrome-doesnt-launch-on-linux

```sh
sudo apt -y install ca-certificates fonts-liberation libasound2t64 libatk-bridge2.0-0 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgbm1 libgcc1 libglib2.0-0 libgtk-3-0 libnspr4 libnss3 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 lsb-release wget xdg-utils
```

#### Fish (Shell)

###### Install Fish

```sh
sudo apt -y install fish
```