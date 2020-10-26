# Stretch Goal: Deployment with Eureka

### VIDEO DEMO: Setting Up a Eureka Instance
[![](video-player.png)](https://drive.google.com/file/d/16J2NfjMF8maGopameIkYJ-GalaOFvuVt/view?usp=sharing)

### VIDEO DEMO: Using Eureka Client
[![](video-player.png)](https://drive.google.com/file/d/1b8jrsA_PKLhvYMbdgzzCEvnTdlkR7jdN/view?usp=sharing)

### VIDEO DEMO: Connecting to PCF Eureka
[![](video-player.png)](https://drive.google.com/file/d/1gZmHdqDL9_iT5H9njJhDl_YUgsOiH8ck/view?usp=sharing)

## Objective
Follow the steps of the above videos to connect to the Eureka service `test-registry` and call the `service-to-call`, only use the GitLab CI/CD and T-Mobile templates to deploy your application.

The required template settings are as follows:
```java
PCF_API: "https://api.sys.px-npe03d.cf.t-mobile.com"
DOMAIN: "https://apps.px-npe03d.cf.t-mobile.com"
PCF_ORG: "Workforce-Transformation-Onboarding"
PCF_SPACE: "Cohort-A"
```
### !challenge

<!--'type' is required-->
<!--'id' is required, string, must be unique within a branch-->
<!--'title' is required, string, used when displaying results-->

* type: project
* id: 97feeef6-07a4-4245-b883-bd43995d3972
* title: Gitlab submission

<!--'question' is required, markdown, the question to be answered-->

##### !question

### Project Submission

Submit the Gitlab link containing your work below.

##### !end-question

<!--'placeholder' is optional, the placeholder text in the input field. -->

##### !placeholder

https://gitlab.com/<username>/<project>

##### !end-placeholder

### !end-challenge