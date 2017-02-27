# Concrete Platform's Base Debian Docker Image

```bash
IMAGE_TAG=some_name

# Build
docker build -f ./builder/Dockerfile -t $IMAGE_TAG . --no-cache

# Run
docker run -d \
           --name $IMAGE_TAG \
           --cap-add=SYS_ADMIN \
           --cap-add DAC_READ_SEARCH \
           --tmpfs /run \
           --tmpfs /run/lock \
           --tty \
           --log-driver=journald \
           --log-opt \
           -v /sys/fs/cgroup:/sys/fs/cgroup:ro \
           $IMAGE_TAG:latest


# Development Build
docker  build --no-cache \
             -f ./builder/Dockerfile \
             -t $(basename $(pwd)):$(git rev-parse --abbrev-ref HEAD)-$(git rev-parse --short HEAD) . \
             --no-cache
```
