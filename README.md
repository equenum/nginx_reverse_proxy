# nginx_reverse_proxy

### NGINX

- Repo: https://github.com/nginx/nginx.
- Docs: https://docs.nginx.com/.

### Useful materials:

- [What is a reverse proxy? | Proxy servers explained](https://www.cloudflare.com/learning/cdn/glossary/reverse-proxy/).
- [What Is a Reverse Proxy Server?](https://www.nginx.com/resources/glossary/reverse-proxy-server/).
- [What is Nginx?](https://medium.com/@sami.alesh/what-is-nginx-7db76b2e79f8) by Sami Alesh.
- [NGINX Product Documentation](https://docs.nginx.com/).
- [Installing NGINX Open Source](https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-open-source/).
- [NGINX Tutorial for Beginners](https://www.youtube.com/watch?v=9t9Mp0BGnyI&t=612s) by freeCodeCamp.org.
- [Configure NGINX as a Reverse Proxy](https://www.youtube.com/watch?v=lZVAI3PqgHc) by NGINX.
- [Nginx: Everything about proxy_pass](https://dev.to/danielkun/nginx-everything-about-proxypass-2ona) by Daniel Albuschat.
- [proxy_pass official documentation](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/).
- [HTTP Load Balancing](https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/).

### Run locally

Run NGINX in Docker:

```shell
docker run -it --rm -d -p 8080:80 --name web nginx
```

Using VSCode + Docker extension (by Microsoft) go to the container to edit files.

Find the files of interest:

- The main `index.html`: /usr/share/nginx/html.
- `default.conf`: /etc/nginx/conf.d/default.conf.
- `nginx.conf`: /etc/nginx/nginx.conf.

Reload NGINX to apply changes via `docker exec` or Docker Desktop => Container => Exec tab:

```shell
nginx -s reload
```

Add new folders and files for testing (find examples in the `assets` folder):

```shell
# create folder
mkdir folderName

#create file
touch fileName.extension
```

To imitate a distributed microservice infrastructure I spun up several api service instances as Docker containers.

Build Docker image:

```shell
cd MediaService.Api
docker build -t media-api -f Dockerfile .
```

Run containers:

```shell
docker run --name media-api-1 -p 5000:8080 media-api:latest
docker run --name media-api-2 -p 6000:8080 media-api:latest
```
