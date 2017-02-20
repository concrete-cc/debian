# Concrete Platform's Base Debian Docker Image

```bash
# Build
docker  build --no-cache \
              -f ./builder/Dockerfile \
              -t $(basename $(pwd)):$(git rev-parse --abbrev-ref HEAD)-$(git rev-parse --short $target_env) .

# Run
docker run -d \
           --name {some_name} \
           --cap-add=SYS_ADMIN \
           --cap-add DAC_READ_SEARCH \
           --tmpfs /run \
           --tmpfs /run/lock \
           --stop-signal=SIGRTMIN+3 \
           -v /sys/fs/cgroup:/sys/fs/cgroup:ro \
           concrete_base_debian:{tag}
```
