Delete docker images:

Will remove ununsed images
docker rmi <<image_id>>
docker image prune -a
docker rmi $(docker images -aq) 

To remove used (used by stopped/running container) images:
docker ps -a
docker stop <<cont_id>> && docker rm <<cont_i>>
docker rmi <<image_id>>

remove image for stopped container: (-f will not work even for running container)
docker rmi -f <<image_id>>


FROM python:3.9

WORKDIR /app/backend

COPY requirement.txt .

RUN pip install -r requirement.txt

COPY . .

docker-compose ups --buid

exec, attach, logs, inspect

