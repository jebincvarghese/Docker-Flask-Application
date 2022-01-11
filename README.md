# Docker-Flask-Application

## Creating a Dockerfile

Create an empty file called Dockerfile:

```
touch Dockerfile
```

Open Dockerfile in your favorite text editor. We first need to define from which image we want to build the image, here I am using Alpine 3.8.

Next we will create a directory to hold the application code inside the image, which will be your application's working directory directory:

```
RUN mkdir /var/flaskapp
    
WORKDIR  /var/flaskapp
```

Copy the entire working directory.

```
COPY . .
```

Install python3 and your app dependencies using the pip3 binary.

```
RUN  apk update && apk add python3

RUN  pip3 install -r requirements.txt
```

Finally, specify the command for starting the application:

```
CMD [ "/usr/bin/python3" , "app.py" ]
```

## Build the Docker Image

Now that the Docker file is complete, it is time to create the Docker image according to the instructions in the file. This is achieved through the Docker build command. 

```
docker image build -t jebincvarghese/devflaskapp .
```

The -t flag lets you tag your image so it's easier to find later using the docker images command.
