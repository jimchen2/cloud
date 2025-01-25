## Certbot

```
sudo systemctl stop firewalld

sudo certbot certonly --standalone -d jimchen.me --email jimchen4214@gmail.com --non-interactive --agree-tos
sudo certbot certonly --standalone -d feed.jimchen.me --email jimchen4214@gmail.com --non-interactive --agree-tos

sudo systemctl start firewalld
```


certbot-renew.timer
## Miniflux

```sh
docker run -d \
  --restart always \
  -p 3000:8080 \
  --name miniflux \
  -e DATABASE_URL="postgresql://" \
  -e RUN_MIGRATIONS=1 \
  -e CREATE_ADMIN=1 \
  -e ADMIN_USERNAME=admin \
  -e ADMIN_PASSWORD= \
  docker.io/miniflux/miniflux:latest
```

## jimchen.me

```
sudo docker run -d --restart always -p 3001:80 -e MONGODB_URI= jimchen2/my-website
```

## nginx

```
sudo ln -sf /etc/nginx/sites-available/jimchen.me.conf /etc/nginx/sites-enabled/
sudo ln -sf /etc/nginx/sites-available/feed.jimchen.me.conf /etc/nginx/sites-enabled/
```