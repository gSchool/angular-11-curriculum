# Project
Consume an external api using Angular 
 
Assignment: 
Create an Angular app that consumes an at least two APIs and displays the results in  CSS styled collections in your application. 

Requirements and grading : 100 possible points

Application uses dedicated component for resource fetched from API (planes component for planes, students component for students, etc.) : 10 points

Http is correctly set up in app.module.ts and within the project: 10 points

CSS styling is used throughout the app : 10 points

Application iterates over collection : 10 points 

Application uses a service to make api calls : 20 points

Application uses models to anticipate shape of data coming in from API: 20 points 

Application consumes two external APIs: 20 points 





You are free to use this one: 
[https://nestjs-typeorm-postgres.herokuapp.com/flights](https://nestjs-typeorm-postgres.herokuapp.com/flights)

or choose one from this list: 
[https://gitlab.com/nmuta1/public-apis/-/blob/master/README.md](https://gitlab.com/nmuta1/public-apis/-/blob/master/README.md)

## IMPORTANT ! 
You may run into CORS errors when accessing an external API while running a local Angular project. Ask your instructor to provide a quick lecture on CORS.  There are many ways around this, but one easy way is to use a CORS proxy like CORS ANYWHERE. Please be mindful that this is a public resource that was made for students and should not be abused or used on high-volume, commercially facing sites. 

Here's how you use CORS ANYWHERE: prefix the url that your http service is hitting with _https://cors-anywhere.com_ . 

Example: You want to use 
```
https://animechan.vercel.app/api/random
```
but you're getting a CORS error. 

Change your URL to 

```
https://cors-anywhere.com/https://animechan.vercel.app/api/random
```

And it should work. You can also use the [CORS plugin for Chrome](https://chrome.google.com/webstore/detail/allow-cors-access-control/lhobafahddgcelffkeicbaginigeejlf?hl=en). 

### !challenge
* type: project
* id: III654DE-4B2U-UB0A-B577-ANG7NGPROJEC
* title: Unit one exercise


##### !question
## StackBlitz project
Enter the URL of your StackBlitz Angular project
##### !end-question

##### !placeholder
StackBlitz URL of your project
##### !end-placeholder

##### !explanation
Thank you for your submission! 😀
##### !end-explanation
### !end-challenge
