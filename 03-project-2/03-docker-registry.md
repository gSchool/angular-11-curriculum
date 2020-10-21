## Share Images with a Registry

So you've created an image for your application. Now you need to upload it somewhere so that your team can use it and deploy it.

For this, we use a **registry** which, in plain terms, is a cloud service that hosts all of your docker images. A team can set up a registry server that stores and provides your collection repositories. Each repository can contain any number of docker images.

### More on Images

Images are represented by the tag names you've been creating, such as 'latest'. Adding a new image to a repository is as simple as giving it a new tag. 

We can think of tags as different versions of the app. You can imagine a repository might have beta, dev, and production tags for any given version of your application.

### Docker Hub

If you don't already have a Docker Hub account, let's make one now. The Hub provides a registry service for free.

1. Go to: https://hub.docker.com/ to create an account
2. By default there should be a repository with your username. If not, create one with any name you like.
2. In your terminal, login: `docker login`

Finally, let's make sure our image has been created and then push it to the Registry:
```
# Step 1: Create a new build
docker build -t your_repo_name/apidemo:latest .

# Step 2: Look for your_repo_name/apidemo Docker Repository with tag 'latest'
docker image ls

# Step 2: Push! This may take a minute so give it time.
docker push your_repo_name/apidemo:latest
```

You should now be able to see your repository online in the Registry! Visit the registry and find your app. Explore the interface and learn more about what's there. 

From now on, you can pull and run this repository from the CLI instead of locally:

`docker run -p 4000:8080 your_repo_name/apidemo:latest`

...and that's the very magic of Docker! Sharing is simpler. Your teammates don't need to install or setup anything to run this app. They simply need Docker and then they can run images straight from the repository.

