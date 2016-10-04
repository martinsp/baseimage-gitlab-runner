# baseimage-gitlab-runner

Dockerfile based on [gitlab-ci-multi-runner Dockerfile](https://gitlab.com/gitlab-org/gitlab-ci-multi-runner/blob/master/dockerfiles/ubuntu/Dockerfile) using [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker) as base image.

## Building container

```shell
docker build -t baseimage-gitlab-runner .
```

## Running container

Adjust `$HOME/baseimage-runner/config` for your needs or create that path to persist gitlab-runner's configuration with `mkdir -p $HOME/baseimage-runner/config`

```shell
docker run -d --name baseimage-gitlab-runner \
  --restart always \
  -v $HOME/baseimage-runner/config:/etc/gitlab-runner \
  -v /var/run/docker.sock:/var/run/docker.sock \
  baseimage-runner
```

## Registering runner with GitLab ci

```shell
docker exec -it baseimage-runner gitlab-runner register
```
