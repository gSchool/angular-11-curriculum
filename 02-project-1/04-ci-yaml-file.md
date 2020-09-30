## The .gitlab-ci.yaml file 


The presence of a .gitlab-ci.yaml file in a repository is what gives GitLab the signal that we will be using CI / CD for this particular project. 

The core functionality of this first .gitlab-ci.yaml file that we are going to build includes: 

- building the image
- compiling and testing the code
- creating artifacts
- pushing the code to production


#### Video: Setting up the gitlab-ci.yaml file 
[![](video-player.png)](https://youtu.be/w2hdFxbRQkY) 

#### Video: Using GitLab's built-in ci linter tool for your project:  
[![](video-player.png)](https://youtu.be/nwXJgDM3R4I) 

Please use the following .gitlab-ci.yml code to answer the challenge questions below: 

```yaml
  cache:
  paths:
  - /usr/local/lib/node
  - node_modules

stages:
- compile
- test
- deploy


build:
  stage: compile
  image: node:12-stretch
  script:
  - 'npm ci'
  - 'npm install -g @angular/cli'
  - 'ng build'
  artifacts:
    paths:
    - dist/

test:
  stage: test
  image: jramcast/karma-chrome-xvfb
  script:
  - 'npm install -g @angular/cli'
  - 'ng test'

deploy:
  stage: deploy
  script:
  - curl --location "https://cli.run.pivotal.io/stable?release=linux64-binary&source=github" | tar zx
  - ./cf login -u $CF_USERNAME -p $CF_PASSWORD -a api.run.pivotal.io
  - ./cf push
  only:
  - master
  
```


### !challenge

* type: short-answer
* id: B308C9C1-315A-4CFD-A21D-33C4654F4B45
* title: .gitlab-ci.yml file
* topics: ci, cd

##### !question

What is the name of the Docker image that is used to run tests in this .gitlab-ci.yml file?

##### !end-question

##### !answer
* jramcast/karma-chrome-xvfb

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, users can see after a failed attempt) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

There are two docker images used in this file, the 2nd of which is in the test section. That image is used to run tests because it contains things like Chrome and Karma that will be used to run Angular tests for this code base. 

##### !end-explanation

### !end-challenge

////////

### !challenge

* type: short-answer
* id: AEB95E4C-522E-43B3-8A52-B32202889ED5
* title: .gitlab-ci.yml file
* topics: ci, cd

##### !question

What is the purpose of the artifacts section in this file?

##### !end-question

##### !options

* passing on the dist folder to the next pipeline stage
* logging build artifacts to the console
* passing on artifacts to CI
* logging old artifacts that are no longer needed

##### !end-options


##### !answer
* passing on the dist folder to the next pipeline stage

##### !end-answer

##### !explanation

Artifacts in a .gitlab-ci.yml file pass on build artifacts to the next stage of pipelines.

##### !end-explanation

### !end-challenge

