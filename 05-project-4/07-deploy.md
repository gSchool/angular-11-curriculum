## Deploy your app to Conducktor

In this lesson, we will take an application and deploy it to Conducktor. You will, ideally, be able to deploy a backend Spring Boot microservice _and_ a frontend Angular application that will talk to each other within our provisioned Conducktor namespace at T-Mobile. 

Deploying to Conducktor takes a lot of steps. Be patient with yourself, allow for error, and keep working through all of these exercises until you get the deployment right. In the end, you will gain a better understanding of how things are set up in Conducktor and you will be one step closer to understanding how microservice deployments work within T-Mobile's Conducktor ecosystem. 

 Note: if you need to encode to base64 on a Windows environment, you can use [base64encode.org](https://www.base64encode.org/)


<table>
<tr><th> video </th><th> description </th></tr>
<tr>
<td> 
  <a href='https://youtu.be/7VgrSIiaCVA'> <img src="video-player.png"> </a>
</td> 
<td>Containerizing an Angular app for deployment to Conducktor </td>
</tr>

<tr>
<td> 
 <a href='https://www.youtube.com/watch?v=g2-_jMS64Uc'> <img src="video-player.png"> </a>
</td> 
<td>Creating our project in our T-Mobile workspace on Gitlab </td>
</tr>

<tr>
<td> 
  <a href='https://www.youtube.com/watch?v=Rl2GHzDZAes'> <img src="video-player.png"> </a>
</td> 
<td>Setting up environment variables in Gitlab for Conducktor  </td>
</tr>

<tr>
<td> 
  <a href='https://www.youtube.com/watch?v=zPsN9bay6rQ'> <img src="video-player.png"> </a>
</td> 
<td>Adding the .gitlab-ci.yml file. THIS VIDEO IS OPTIONAL! If you don't want to hear the boring details about this file, you can just copy the file from the section at the bottom of the page and skip this video. Make sure to run it through a linter if the formatting gets messed up in the copy / paste process.  </td>
</tr>

<tr>
<td> 
  <a href='https://www.youtube.com/watch?v=K0R7FTCGtyo'> <img src="video-player.png"> </a>
</td> 
<td>Adding the JINJA file ( dev_deploy_info.yaml.j2 ) the file extension must end in j2 and match what's in your .gitlab-ci.yml file (see below).  </td>
</tr>


<tr>
<td> 
  <a href='https://www.youtube.com/watch?v=hC2iHjLNLvY'> <img src="video-player.png"> </a>
</td> 
<td>Adding our Conducktor secrets and creating our .j2 file. This is the most intricate of all of the videos. Do not skip this video! Please watch carefully.  </td>
</tr>

<tr>
<td> 
  <a href='https://www.youtube.com/watch?v=p-_kNAcPxtQ'> <img src="video-player.png"> </a>
</td> 
<td> Adding some final variables and pushing everything to GitLab to watch pipelines  </td>
</tr>

<tr>
<td> 
  <a href='https://www.youtube.com/watch?v=5idi_SPRfyM'> <img src="video-player.png"> </a>
</td> 
<td> Debugging pipelines  </td>
</tr>

<tr>
<td> 
  <a href='https://www.youtube.com/watch?v=SNV7N7yntpk'> <img src="video-player.png"> </a>
</td> 
<td> Fixed pipelines and final deployment  </td>
</tr>






 </table>
 




 

.gitlab-ci.yml file: 

```
include:
  - project: 'tmobile/templates'
    ref: tmo/master
    file: '/gitlab-ci/.tmo.global.common.gitlab-ci.yml'
      
  - project: 'tmobile/templates'
    ref: tmo/master
    file: '/gitlab-ci/.tmo.job.npm.gitlab-ci.yml'
  
  - project: 'tmobile/templates'
    ref: 'tmo/master' 
    file: 'gitlab-ci/.tmo.job.docker.gitlab-ci.yml'

  - project: 'tmobile/templates'
    ref: 'tmo/master' 
    file: 'gitlab-ci/.tmo.job.dockerScan.gitlab-ci.yml'


  - project: 'tmobile/templates'
    ref: tmo/master
    file: '/gitlab-ci/.tmo.function.duck-deploy.gitlab-ci.yml'
  
stages:
  - tmo
  - test
  - build
  - package
  - ci
  - deploy
  
# put these above any custom jobs 
variables:
  # how registry image gets named and semantically versioned.
  EXTRA_DOCKER_TAG: "$CI_REGISTRY_IMAGE/$CI_COMMIT_REF_SLUG:$CONTAINER_VERSION.$CI_PIPELINE_IID"

  
deploy-dev:
  stage: deploy
  extends: .duck_deploy
  # this part was outdated in the docs ( below )
  variables:
    CONDUCKTOR_CONFIG_PATH: ./dev_deploy_info.yaml
    GIT_DEPTH: 1
    CONDUCKTOR_NS: wfo-dev-duck-dev-w2
    CONDUCKTOR_TARGET: duck-dev-w2 
  environment:
    name: dev

```
