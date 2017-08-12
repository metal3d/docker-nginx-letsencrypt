# Nginx with certonly from Let's Encrypt

This is an override of nginx container with certbot to be able to be certified by let's encrypt.

A volume is also created to be able to store certificates outside the container: /etc/letsencrypt

To get this image:

```bash
docker pull metal3d/nginx-letsencrypt
```

Then start it with volumes to configure nginx, and store certificates:

```bash
docker run --name="nginx" \
    -v ./letsencrypt:/etc/letsencrypt \
    -v ./conf.d:/etc/nginx/conf.d \
    metal3d/nginx-letsencrypt
```

To certify or renew you website:

```bash
docker exec -it nginx certbot certony ...
docker exec -it nginx certbot renew ...
```


