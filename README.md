docker-compose up --build

pm2 for production

Once your images are on Docker Hub, you can update your Docker host to pull the new images and restart the containers. For this part, you can use a simple shell script on your Docker host that does the following:

Log in to Docker Hub.
Pull the new images.
Bring down the current containers.
Bring up the new containers.
For example:

bash
Copy code
#!/bin/bash
docker login -u $DOCKER_HUB_USERNAME -p $DOCKER_HUB_ACCESS_TOKEN
docker pull $DOCKER_HUB_USERNAME/myapp-client:${IMAGE_TAG}
docker pull $DOCKER_HUB_USERNAME/myapp-server:${IMAGE_TAG}
docker-compose down
docker-compose up -d
