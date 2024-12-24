![[Pasted image 20241202055606.png]]

### Most Used Commands

build image: docker build -t <name> .
run container: docker run -i -t -p 3001:3001 <name>

list running containers: docker ps
list built images: docker images

delete container: docker rm -f <container_id>
delete image: docker image rm -f <image_id>