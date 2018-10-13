Reverse proxy
-----------------
Docker compose configuration for reverse proxy. Nginx proxy + letsencrypt image for renew certificates.

How to run
-----------------

1.Clone repository  

2.Configure environment variables  
`DEFAULT_HOST` - is using for set domain names.   
More details https://github.com/jwilder/nginx-proxy#multiple-hosts  

3.Run command
```bash
docker-compose up
```

4.Then start any containers you want proxied with an env vars:  
 `VIRTUAL_HOST=youdomain.com`  
 `LETSENCRYPT_HOST=youdomain.com,www.youdomain.com,mail.youdomain.com`  
 `LETSENCRYPT_EMAIL=foo@bar.com`  
     
```bash
docker run -e VIRTUAL_HOST=foo.youdomain.com  ...
```

Help commands
-----------------

Check docker and docker-compose version
```bash
docker --version
docker-compose --version
```

Check docker-compose file configuration
```bash
docker-compose config
```

View certificates information from letsencrypt container
```bash
docker exec nginx-letsencrypt /app/cert_status
```

Renew certificates in letsencrypt container
```bash
docker exec nginx-letsencrypt /app/force_renew
```
