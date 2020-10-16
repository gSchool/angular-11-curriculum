## Creating a Docker Image

Now that you've installed Docker have seen how it works, we'll get started by creating our own Docker image.

1. Make sure you've cloned [this repository](https://gitlab.com/nmuta-jones-tmo/heroku-spring)
2. Add a new file to it named `Dockerfile`
3. Open the project in your code editor and edit the `Dockerfile`.
4. Copy and paste the following into it:

```Dockerfile
# Use Open JDK as base image
FROM openjdk:8-jdk-alpine
# Set the working directory
WORKDIR /

# Take the jar from the build folder and add it to project as springweb.jar
ADD build/libs/springweb-0.0.1-SNAPSHOT.jar springweb.jar

# Expose PORT 8080
EXPOSE 8080

# Invoke java executable and run the springweb.jar file
CMD java -jar springweb.jar
```

Read the comments of the file to understand what each command is doing. 

**Dockerfile**s are used to define how your application should run. Everyone on your team will use this to run and/or deploy this app as a service.

Finally, build and run the app: 

```bash
# Step 1: Build. Think of the tag as the build version for the Docker Image. The period at the end means "here", the current directory.
docker build -t apidemo:latest .

# Step 2: Run apidemo. Flag for instant removal (--rm) run on port 8080, and name the instance apiContainer 
docker run --rm -p 8080:8080 --name=apiContainer apidemo

# OR run as a detached container instead, which does the same thing. Try both!
docker run -d -p 8080:8080 --name=apiContainer apidemo

# Step 3: Open your browser to localhost:8080 to see your app running.

# Step 4: Stop your container (stop it with the name we provided ) 
docker container stop apiContainer

```

> NOTE: If you don't provide a tag (image name) Docker assumes 'latest'. Make sure you're working from the correct image! Here we are working from apidemo:latest even though we didn't provide 'latest'.

### VIDEO DEMO: Dockerizing a simple Python HTTP Server

[![](video-player.png)](https://drive.google.com/file/d/1uGwCTZZ8hdpNxHjk8YLC3Bu6nR1Ad9Mg/view?usp=sharing) 




You've built a Docker app. But you're using Docker for a reason: to share and collaborate. Next we'll talk about how to share your apps.




