## Use Ubuntu

## Certbot

```
sudo mkdir -p /var/www/html
sudo chown -R www-data:www-data /var/www/html

sudo certbot certonly --webroot -w /var/www/html -d jimchen.me
sudo certbot certonly --webroot -w /var/www/html -d feed.jimchen.me
```

## Cert Renew

```
sudo certbot renew --dry-run
sudo certbot renew --force-renewal
```


## nginx

```
sudo ln -sf /etc/nginx/sites-available/jimchen.me.conf /etc/nginx/sites-enabled/
sudo ln -sf /etc/nginx/sites-available/feed.jimchen.me.conf /etc/nginx/sites-enabled/
```

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
