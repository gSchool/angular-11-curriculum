## Stretch goal : Using Docker to mount your project onto an image 

## NOTE: THIS EXERCISE IS OPTIONAL !  ONLY DARE TO DO THIS IF YOU ARE READY FOR A SMALL CHALLENGE !  

Pipelines can take a long time to complete. There are several shortcuts that may help you obtain faster builds.  However, the fastest way to simulate what the pipelines are doing is to run them locally from your own machine.  Docker can help make this possible. 

The video below demonstrates how you can use disk mounting with Docker to optimize the testing process before pushing your project to GitLab.

Watch the video below. Then obtain a Docker image that has tests in it, mount the image locally on your machine, and run the tests as shown below. When you are comfortable with this process, record the procedure, upload it to the cloud ( YouTube, Google Drive, etc.) and paste the link of the uploaded video below. 

### VIDEO: Docker as a development environment

[![](video-player.png)](https://drive.google.com/file/d/19xdt7p7m5XtNoZxlbnhmj0GzJgokpObc/view) 

### !challenge
* type: project
* id: AD7654DE-4B22-4B0A-B577-TMO2P2EXERCI
* title: T-MOBILE p2 d1: Docker as dev env

##### !question
## URL of you using docker file mounting
Paste the URL of docker dev env video
##### !end-question

##### !placeholder
URL of the docker dev env video
##### !end-placeholder

##### !explanation
Thank you for your submission! 😀
##### !end-explanation
### !end-challenge


#### HINT
If you are Dockerizing an Angular container that has Karma tests in it, you may get an error when trying to run that in a container because your container cannot find Chrome. 

You may need to run a headless version of Chrome to get this working. Look at 
[this karma.conf.js file](https://gitlab.com/nmuta-jones-tmo/coincounter/-/blob/master/karma.conf.js) and compare it with yours. Do you see a difference ? 

Why do you need to use a headless browser ?  If you think about it, your Linux instance that the container is based on does not have a full version of Chrome installed on it. Why would a container need a full web broswer ?  This uses a slimmed down version of Chrome running in the background (i.e. 'headless' ) and it uses that to run your tests.  





 



