## The gitlab-ci.yaml file 


The presence of a gitlab-ci.yaml file in a repository is what gives GitLab the signal that we will be using CI / CD for this particular project. 

Remember when we talked about how Docker images will "build" a Docker project based on a core image that contains the base technologies needed to kickstart a project ? 

The CI yaml file follows that same pattern. 

The core functionality of this first gitlab-ci.yaml file that we are going to build includes: 

- building the image
- compiling and testing the code
- creating artifacts
- pushing the code to production


Fork and clone the repo that you are most interested in deploying: 

[Java Spring](https://gitlab.com/tmo-spring-ci-starter-2020)

[Angular](https://gitlab.com/tmo-angular-ci-starter-2020)


#### Video: Continuous delivery deployment targets
[![](video-player.png)](https://youtu.be/tXtPJPCzSTY) 



#### CFU placeholder