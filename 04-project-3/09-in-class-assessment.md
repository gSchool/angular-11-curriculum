# In-Class Assessment

# Checkpoint

For this assessment you will be deploying a provided application to PCF.

First, clone [this project](https://gitlab.com/tmobile/workforce-transformation/onboarding-bootcamps/cohort-1-exercise-submissions/hello-world).

Then, create a `manifest.yml` file. Put in the base requirement for the application and name it with your first name, followed by the initial of your last name, followed by a dash and application in all caps. The name should look like `JOHND-APPLICATION`.

Next, create a .gitlab-ci.yml file and include jobs from the templates of Common, Gradle, SonarScanner, Fortify, and PCF. Use these values for the mandatory PCF variables—the remaining mandatory variables have been filled out in the group variables.

`Note:` SonarScanner outputs error logs as comments on your commits. Also, do not specify a PCF Blue/Green strategy.

```java
PCF_API: "https://api.sys.px-npe03d.cf.t-mobile.com"
DOMAIN: "https://apps.px-npe03d.cf.t-mobile.com"
PCF_ORG: "Workforce-Transformation-Onboarding"
PCF_SPACE: "Cohort-B"
```

Finally, create a repository in GitLab, change the origin to the new link, and push up your code.

After pushing the assessment to GitLab, you can find the link to your application by going to `CI/CD > Jobs`. Then select the deploy-dev job. Within the logs there is a route which will be the URL to your application.

### !challenge

<!--'type' is required-->
<!--'id' is required, string, must be unique within a branch-->
<!--'title' is required, string, used when displaying results-->

* type: project
* id: f104fda2-7bf2-4aa0-a3e3-d9b7e102781c
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

