# Backand Core


### Steps to use
- Change `CONTAINER_PREFIX` in .env in the root of project and other params if you need
- Rename service's prefix in file `docker/nginx/conf.d/project.conf` in line `fastcgi_pass prefix-php:9000;` from `prefix-php:9000;` to `my-project-prefix-php:9000;`
- Configure `.env` in api directory 