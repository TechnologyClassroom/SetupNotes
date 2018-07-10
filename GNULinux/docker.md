# Docker

Docker is a popular container system.

[Docker Community Edition (CE)](https://www.docker.com/community-edition)

[Docker Documentation](https://docs.docker.com/)

[Docker Hub](https://hub.docker.com/)

## Installing Docker

[CentOS install Guide](https://docs.docker.com/install/linux/docker-ce/centos/)

[Debian install Guide](https://docs.docker.com/install/linux/docker-ce/debian/)

[Ubuntu install Guide](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

## Running Docker

- Enable docker service with systemd.

```
systemctl enable docker
```

- Start docker service with systemd.

```
systemctl start docker
```

- Add a user to the docker group.

```
usermod -a -G docker usernamehere
```

- List docker containers on the system.

```
docker image
```

- Search for containers matching a keyword.

```
docker search ubuntu
```

- Install a container.

```
docker pull hello-world
```

- Run a container.

```
docker run hello-world:latest
```

- View configuration information of a container.

```
docker inspect hello-world
```
