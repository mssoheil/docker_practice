# every line is a layer to the image
# parent image (layer)
FROM node:17-alpine

RUN npm install -g nodemon
# move to app directory for every line after
WORKDIR /app
# copy sth in to the image
# relative path of directory that we want to copy from
# we do this so we can cache packages for faster build
COPY package*.json .
# dependencies
RUN npm install
# copy into root directory
# COPY . .
# copy to app directory
COPY . .
# used for port mapping in docker deskgop(optional for command prompt run)
EXPOSE 4000
# specify any commands that should be run at run time when the container begis to run
# equivalant of node app.js command
# CMD ["node", "app.js"]
CMD ["npm", "run", "dev"]
# -t -> tag (give the image a name)
# . -> relative path to dockerfile from the directory we're in the terminal

# ------------------- some docker commands --------------------

# building using Dockerfile
# docker build -t myapp .

# running image with given container name -d means detached mode so it won't block the terminal (it creates a container)
# --rm -> remove container when we stop the image
# -v ABSOLUTE_PATH_OF_PROJECT_FOLDER:PATH_OF_WORKDIR to map a folder of our computer to the image folder - for e.g. usefull for using nodemon so the changes of our folder in the computer reflects the image the second -v /app/node_modules is used so node_module don't change the image
# docker run --name myapp_c1 -p PORT_IN_COMPUTER:PORT_EXPOSED_BY_CONTAINER -d --rm -v ABSOLUTE_PATH_OF_PROJECT_FOLDER:PATH_OF_WORKDIR -v PATH_OF_WORKDIR/node_modules myapp

# docker processes list of container (that currently are running) by adding -a we tell docker to list all of containers(running or not)
# docker ps

# stop a process
# docker stop [containerId or containerName]

# restart a existing container
# docker start [containerId or containerName]

# list of all of the images
# docker images

# remove an image -f will force delete even if that image is used in a container
# docker image rm [ImageName or ImageId] -f

# delete a container
# docker container rm [containerId or containerName]

# delete every image and container and volumes to be able to work from the scratch
# docker system prune -a

# run shell so for e.g. we can run ls
# docker exec -it [containerId or containerName] sh