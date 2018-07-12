# Jenkins: Install in Docker Demo

## 安装 Docker

- [Get Docker](https://docs.docker.com/install/)

## 使用 Docker 安装 Jenkins

```bash
docker run \
  --name jenkins-blueocean \
  -u root \
  --rm \
  -d \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins-data:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkinsci/blueocean
```