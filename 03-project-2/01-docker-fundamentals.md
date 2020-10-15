## Docker fundamentals


Take 5 minutes to [download and install Docker on your local machine.](https://docs.docker.com/engine/installation/)

Then check to make sure it's up and running:

```
# check docker version
docker --version

# view info about your installation
docker info

# run the test image and view a list of currently installed images
docker run hello-world
docker image ls
docker container ls --all
```
If this doesn't work, let your instructors know.

## Images and Containers

**Images** represent your application package and it's setup and configuration are defined within the Dockerfile.

**Containers** are *running instances* of your application image. 

What makes containers so consistent for you and your team is that Docker handles the environment setup so that all anyone has to do to run the app is run a Docker container.

Let's try it.

## Running a Docker App

Now that you have Docker installed, let's see just how easy it is to use an existing application. Pull and run ths project from Docker:

```
# Tell Docker to pull a simple html app repository with tag 'latest' and run it 
# locally on port 8080. ( 8080 on your machine and 8080 from the container ) 
docker container run --rm -it -p 8080:8080/tcp nmuta/python_serv:latest
```

You should see some header text that says

```
Congratulations! 
```
With some other text on the page. This image has been pulled from a public repo and is now running locally on your computer. It is a simple HTML page being served up with a python server, but you do NOT need Python to be installed on your machine, you don't need the files, all you need is Docker, which runs this container. The container is "self contained" ( pun intended ), and it has everything it needs to serve the application. All you need to do is run it.  Magic! 

With this simple command as a developer you were able to avoid:

- cloning a repository
- install dependencies
- configure a server

This is why Docker is a great tool for collaboration and service management. It automates processes to make managing services and deploying them simple and fast.

The application you just ran is an example of what you'll be creating for this lesson. Even though it's pretty minimal, alot of configuration will go into making this work. 

### Trouble-shooting

Here's some common issues you may run into while learning Docker, along with some ways to troubleshoot.

**Tip 1: Docker connection issues**
If the docker server seems to be down or you're getting errors that say docker isn't running, first try closing your terminal session out and starting a new one. Then run `docker info` or `docker version` to check if it's running.


 
