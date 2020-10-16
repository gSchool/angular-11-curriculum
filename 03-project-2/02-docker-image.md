## Creating a Docker Image

Now that you've installed Docker have seen how it works, we'll get started by creating our own Docker image.

<<<<<<< HEAD
1. Make sure you've cloned this repository. (TODO @nmuta : LINK?)
=======
1. Make sure you've cloned [this repository](https://gitlab.com/nmuta-jones-tmo/heroku-spring)
>>>>>>> f3f4569cd5b3480142efddf612b4b087529d2b75
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

**Dockerfile**s are used to define how your application should run.  

Finally, build and run the app: 


### Step 1: Build. 
Think of the tag as the build version for the Docker Image. 
The period at the end means "here", the current directory.
docker build -t apidemo:latest .

### Step 2: Run apidemo. 
Flag for instant removal (--rm) run on port 8080, and name the instance apiContainer 
```bash
docker run --rm -p 8080:8080 --name=apiContainer apidemo
```

### OR run as a detached container instead, which does the same thing. Try both!
docker run -d -p 8080:8080 --name=apiContainer apidemo

### Step 3: Open your browser to localhost:8080 to see your app running.
You should see a default error landing page that looks like this: 


![](springLanding.png)

 

That means you are succesfully running your Java Spring Boot container and it is being displayed on port 8080 in your browser. 

When you visit this route: 
```
http://localhost:8080/movies
```
 

You should see a list of movies as such: 
```
[
 {
  "id": 1,
  "title": "Lion King"
 },
 {
  "id": 2,
  "title": "Daughters of the Dust"
 },
 {
  "id": 3,
  "title": "Quilombo"
 }
]
```

We are hitting the '/movies' endpoint and getting data. This data is not coming from a database ( yet ) ; it is simply being served from a static array in a Spring Boot app controller which is running in the container.  


 
### Step 4: Stop your container (stop it with the name we provided ) 

```bash
docker container stop apiContainer
```

> NOTE: If you don't provide a tag (image name) Docker assumes 'latest'. Make sure you're working from the correct image! Here we are working from apidemo:latest even though we didn't provide 'latest'.

If you would prefer to see a live video of this entire process of Dockerizing a Java app, the video below shows that process. If you already feel comfortable, feel free to skip over the Java video and go straight to the *Dockerizing a simple Python HTTP Server* video to continue this lesson. 


### OPTIONAL VIDEO : Dockerizing the Java Spring app 
[![](video-player.png)](https://drive.google.com/file/d/15GY-d7sVbpwxGufHigxAxy5BMVzEyMoX/view) 



### VIDEO DEMO: Dockerizing a simple Python HTTP Server
[![](video-player.png)](https://drive.google.com/file/d/1uGwCTZZ8hdpNxHjk8YLC3Bu6nR1Ad9Mg/view?usp=sharing) 



After finishing this unit, you should feel comfortable adding Docker files, building Docker images, running Docker containers locally on a port ( if applicable ), and stopping containers. You should repeat this process until you feel comfortable with the mechanics of everthing. 


In the next unit we will talk about how to share your apps.


