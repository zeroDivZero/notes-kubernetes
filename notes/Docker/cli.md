# CLI

## `docker info`

Displays sys info.

## `docker version`

Displays sys ver.

## `docker login`

Logs in to Docker registry (default Docker Hub).

## `docker pull IMAGE`

Pulls image from registry.

## `docker run [OPTIONS] IMAGE [COMMAND] [ARGS...]`

Runs command in new container.

* `-d` (`--detach`): Run in detached mode (returns control to shell).
* `-p` (`--publish`): Publish container's port(s) to host.
* `--name`: Specify container name, or Docker will assign one.
* `-it`: Attach shell.

    ```sh
    docker run -it nginx -- /bin/zsh
    ```

### Example

Start Apache HTTP server container in detached mode, mapping host port 8080 to container port 80 (routing traffic to host's 8080 to container's 80), naming container `my-httpd`:

```sh
docker run -d -p 8080:80 --name my-httpd httpd
```

### Resource Limits

To set max memory and CPU usage:

```sh
docker run --memory="256m" nginx
docker run --cpus=".5" nginx
```

## `docker start CONTAINER`

Starts stopped container.

## `docker ps`

Lists running containers. Add `-a` to list stopped ones also.

## `docker stop [OPTIONS] CONTAINER [CONTAINER...]`

Stops one or more containers.

## `docker kill [OPTIONS] CONTAINER [CONTAINER...]`

Kills one or more containers. Same as `stop`.

## `docker rm [OPTIONS] CONTAINER [CONTAINER...]`

Removes one or more containers.

* `-f` (`--force`): Force-remove running container (SIGKILL).

### Example

Remove stopped containers:

```sh
docker rm $(docker ps -a -q)
```

## `docker image inspect IMAGE`

Gets image info.
