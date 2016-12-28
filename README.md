# Docker image with consul template binary

A simple image based on alpine, with latest consul-template binary

## How to use ?

Example with restarting a docker container on the host (for example, nginx, where nginx is the container name):

```
docker run -d \
  -v /path/to/templates:/templates \
  -v /var/run/docker.sock:/var/run/docker.sock \
  blackillzone/consul-template \
  -wait=5s \
  -consul localhost:8500 \
  -template "/templates/template.ctmpl:/etc/nginx/conf.d/template_result.conf:docker kill -s HUP nginx"
  -dry
```

## Why not installing it directly in a docker image ?

I want this to be usable, and also to avoid to maintain specifics image with each one their version AND the version of consul-template. If I need to update Nginx, I don't need to rebuild an image, but pull and update the new one :).

**Official documentation**: <https://github.com/hashicorp/consul-template/blob/master/README.md>
