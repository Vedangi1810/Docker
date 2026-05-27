Virtualization vs Containarization
Architecture of Docker:
docker daemon (dockerd and containerd), docker client, docker engine, docker CLI
docker login
docker images
docker ps (sudo usermod -aG docker $USER and newgrp docker)

Dockerfile --build-- image --run-- container

if you update source code in your host/local, run docker build and docker run again
============================================================================================
docker ps
docker logs <cont_id>
docker attach <cont_id>
docker start <cont_id>
docker stop <cont_id>
docker exec -it <cont_id> bash
docker run -itd ubundu (run continously without stopping)
============================================================================================
docker networks:
Host
Bridge (default)
User defined bridge (custom)
None
MACVLAN, IPLAN,Overlay (docker swarm)
============================================================================================
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

