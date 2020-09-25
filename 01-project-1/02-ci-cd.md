### Getting Started with CI / CD 


CI / CD ( Continuous Integration / Continous Delivery ) is one of the cornersontes of the software development lifecycle at T-Mobile. 

*Continous Integration* was born out of the need to scrutinize all code before it gets merged into the commmon code base or branch within an organization. CI is the proces of running builds, tests, and other quality control methods to make sure that developers are not introducing new bugs into shared code, while also making sure that new code does not break existing code. 

The best way to appreciate the value of continuous intergration is to think about what it's like when working on a team of developers who are NOT using CI. Without CI, its very possible for several developers to write new code or modify old code on their respective branche and merge that code into the shared code base only to discover a few days later that "someone" broke the build. Without CI, it can be difficult and time consuming to figure out who that "someone" was. With CI, that "someone" will discover their errors very shortly after they push their code to GitLab or whichever source control hub the organization is using. We will be covering that process in the next unit on pipelines. 

*Continous Delivery* is the process of deploying an applicaiton from GitLab once the CI process is complete. This is ultimately designed to be a time saver. If the code has passed all vetting, it is deemed to be safe to continue its journey in the deployment process. This may mean deploying the code to a staging environemnt, ephermal servers that house temporary builds, or even production in some cases. 

In this unit, you will be creating your own CI / CD pipeline in GitLab. 

#### CFU placeholder