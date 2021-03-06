This is a process wrapper used by 
[the itzg/minecraft-server Docker image](https://hub.docker.com/r/itzg/minecraft-server/)
to ensure the Minecraft server is stopped gracefully when the container is sent the `TERM` signal.

## Development Testing

Start a golang container for building and execution:

```bash
docker run -it --rm \
  -v ${PWD}:/go/src/github.com/itzg/mc-server-runner \
  -w /go/src/github.com/itzg/mc-server-runner \
  circleci/golang:1.10.2
```

Within that container, build/test by running:

```bash
go run test/dump.sh
go run main.go test/bash-only.sh
# The following shoudl fail
go run main.go --shell sh test/bash-only.sh
```