# Concrete Platform's Base Debian Docker Image

IMAGE_TAG=some_name

#BUILD
docker build -f ./builder/Dockerfile -t $IMAGE_TAG ./ --no-cache

#RUN
docker run --name $IMAGE_TAG -d --cap-add=SYS_ADMIN --cap-add DAC_READ_SEARCH --tmpfs /run --tmpfs /run/lock -v /sys/fs/cgroup:/sys/fs/cgroup:ro --tty --log-driver=journald --log-opt tag=$IMAGE_TAG $IMAGE_TAG:latest
