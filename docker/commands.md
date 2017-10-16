View all created containers
```bash
docker ps -a
```
Build and image
```bash
docker build -t jim/node .
```
View all images
```bash
docker images
```
Remove Docker Images
```bash
docker rmi  <IMAGE ID>
```
Delete all untagged images
```bash
docker rmi $(docker images | grep "^<none>" | awk '{print $3}')
```
Delete all stopped containers
```bash
docker rm $( docker ps -q -f status=exited)
```
Delete all dangling (unused) images
```bash
docker rmi $( docker images -q -f dangling=true)
```
Delete all images
```bash
docker rmi $(docker images -a -q)
```
Create app container and link other container to it
```bash
docker run -d --name node -p 7000:7000 --link mongo:mongo --link sad_wescoff:redis jim/node
```
Remove Docker Containers
```bash
docker rm  <CONTAINER ID
```
Stop & Remove All Docker Containers
```bash
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```
Enter a container
```bash
docker exec -it <container id> /bin/bash
```
Copy a file into a container
```bash
docker cp /path/to/filename.ext container_name:/path/to/file/inside/container/filename.ext
```
Create a container passing environmental variables
```bash
docker run -d -name node \
  -e CONSUMER_KEY="" \
  -e CONSUMER_SECRET="" \
  -e ACCESS_TOKEN_KEY="" \
  -e ACCESS_TOKEN_SECRET="" \
  jim/node
```