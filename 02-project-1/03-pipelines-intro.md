## An introduction to CI / CD pipelines


![](pipelines.gif)


Pipelines are a set of checkpoints that you can set up to visualize, analyze, debug, and manage the process of code moving its way through your CI / CD process. 

In this video, we demonstrate how pipelines work, and the general flow of using pipelines in GitLab. 

### !callout-info
# Video: Introduction to pipelines
[![](video-player.png)](https://youtu.be/e1essyyMAcQ) 
### !end-callout



### !challenge

* type: multiple-choice
* id: 00D01B7A-1ACD-484A-9B8C-BD04AAB4BA64
* title: Pipelines
* topics: pipelines

##### !question

What triggers pipelines when you push code to Gitlab?

##### !end-question

##### !options

* pipelines are manually triggered by toggling a button in Gitlab
* any repo with tests in it will trigger pipelines
* pipelines are triggered by pushing to the master branch
* the presence of a .gitlab-ci.yml file triggers pipelines

##### !end-options

##### !answer
* the presence of a .gitlab-ci.yml file triggers pipelines

##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, users can see after a failed attempt) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

the presence of a .gitlab-ci.yml file triggers pipelines

##### !end-explanation

### !end-challenge

