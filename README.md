# Jenkins: Install in Docker Demo

## 感谢

本 Demo 的省略 GUI 安装向导和插件安装的过程，受到了 `foxylion` 的项目启发：

- https://github.com/foxylion/docker-jenkins

## 安装 Docker

- [Get Docker](https://docs.docker.com/install/)

## 构建可自动化配置管理员账号和插件的 Jenkins 镜像

```bash
docker build -t my-jenkins .
```

## 使用 Docker 运行 Jenkins（默认管理员用户名：`admin`，密码：`admin`）

macOS / Linux

```bash
docker run \
  --name jenkins-blueocean \
  -u root \
  --rm \
  -d \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins-data:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  my-jenkins
```

Windows

```bat
docker run ^
  --name jenkins-blueocean ^
  -u root ^
  --rm ^
  -d ^
  -p 8080:8080 ^
  -p 50000:50000 ^
  -v jenkins-data:/var/jenkins_home ^
  -v /var/run/docker.sock:/var/run/docker.sock ^
  my-jenkins
```

如要设置管理员用户名和密码，请在 `docker run` 命令后增加参数：

```bash
--env JENKINS_USER=foo --env JENKINS_PASS=bar
```

随后可以通过如下命令访问容器中的 bash：

```bash
docker exec -it jenkins-blueocean bash
```