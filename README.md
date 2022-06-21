# -Docker-simple-app
Dockerizing simple app into 2 containers

Create Volume to mount to mysql container to make it persistent
docker volume create dbvolume

Create Network to add both containers to be able to talk to each other
docker network create mynet

Spin up the MySQL container
docker run -d --network=mynet -v dbvolume:/var/lib/mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=yes --name=mysql1 mysql:5.7

Build app container using Dockerfile
docker build .

Start container using built image
docker run -d -p 5000:5000 --network=mynet <image-id>
  


