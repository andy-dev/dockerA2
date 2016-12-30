# dockerA2
Angular 2 Docker Simple App


##Docker Ignore
 Before we build the image, if you are keen, you may have noticed that the line COPY . /usr/src/app copies our whole directory into the container, including node_modules. To ignore this, and other files that are irrelevant to our container, we can add a .dockerignore file and list what is to be ignored


##Package.json serving app from host
 To serve the app from host created by docker image

change the start script to

```
 "start": "ng serve -H 0.0.0.0"
 ```

##Build an Image with docker build cmmd

In this case the tag will be angular-client:dev.

The . (dot) at the end refers to current directory. Docker will look for the Dockerfile in our current directory and use it to build an image.

```
$ docker build -t <image_tag>:<tag> <directory_with_Dockerfile>
```

```
$ cd angular-client
$ docker build -t angular-client:dev .
```

Now that the image is built we can run container based on image, The -d flag tells docker to run the container in detached mode. Meaning, it will run and get you back to your host, without going into the container.

```
$ docker run -d --name <container_name> -p <host-port:exposed-port>  <image-name>
```

```
docker run -d --name angular-client -p 4200:4200 angular-client:dev
```

##Stopping Container

```
docker stop angular-client
```

##Remove all Images Container

```
docker rm $(docker ps -a -q)
```

# Delete every Docker image
```
docker rmi $(docker images -q)
```