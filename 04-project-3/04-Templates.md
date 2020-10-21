# Templates

## Learning Objectives

By the end of this lesson you will be able to:

* Understand how to use templates within pipelines

## Template Structure

Templates are pre-built segments of pipelines. T-Mobile uses these templates and has a goal to have all pipelines within the organization using them. To that end, they have different branches for the templates, and anyone within the company can submit changes to be pulled into the master branch.

You can find the templates at https://www.gitlab.com/tmobile/templates

All templates have documentation on how to implement them within your code. They provide a list of mandatory and optional variables that you can use to configure your pipeline. Within the documentation it also provides an `includes` statement that shows how to pull the template into your pipeline.

### VIDEO LESSON: Templates
[![](video-player.png)](https://drive.google.com/file/d/1z6b4ESynMQTfH3ee7lfWr1WOj7CvL9fI/view?usp=sharing)

### Functions and Jobs

Being pulled in by the includes statement, there are functions and jobs. Functions provide the code that is input into your pipeline; you can find them within the gitlab-ci folder inside the templates repository. Jobs implement the functions during different stages of development based upon the branch names used for each push.

<!-- >>>>>>>>>>>>>>>>>>>>>> BEGIN CHALLENGE >>>>>>>>>>>>>>>>>>>>>> -->
### !challenge

* type: checkbox
* id: cdb8544b-0b6d-4ff8-82f3-af1794e015f6
* title: CI/CD Problem Statement

##### !question
Which of the following can you do with the templates?
##### !end-question

##### !options

* Include and implement a function
* Include and implement a job
* Include a function to implement a job when the pushing code
* Include a job to implement a function when the pushing code

##### !end-options

##### !answer

* Include a job to implement a function when the pushing code
* Include and implement a function

##### !end-answer

### !end-challenge

<!-- ======================= END CHALLENGE ======================= -->

These will often also call on scripts, which are located within the script folder on the template repository. They are written in bash and often contribute the majority of getting the templates to work. Being able to read and understand the script level of the templates is key in operating and debugging them.

## Continuous Delivery Platform Team

The Continuous Delivery Platform (CDP) Team is a team within T-Mobile, and they are in charge of the templates. They are available to provide support whenever needed within the `#cdp-support` channel on Slack.

