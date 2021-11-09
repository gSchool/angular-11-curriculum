

# Dependency Injection

Now that we've created a flights service, let's look under the hood and study what actually makes the service work and what allows that service to be used throughout the Angular app. 


Angular services provide data to components using Angular's dependency injection system.  [Dependency injection](https://en.wikipedia.org/wiki/Dependency_injection) is the process of passing a service into a constructor, so that it can be referenced within the context of that class.  Angular will take care of instantiating our service as a singleton, but we'll have to modify the constructors of any component wishing to consume that data ourselves.  

In our [flights application](https://stackblitz.com/edit/angular-ivy-ybkv56?file=src%2Fapp%2Fflights%2Fflights.component.ts) on StackBlitz, in flights.component.ts, we imported the flight service.   This is what our constructor looked like: 

```
constructor(private flightService: FlightService) { }
```

This added a `flightService` property on the flight component.  
We were then able to call *flightService*, which is a local variable that represents an instance of the main FlightService , which is the singleton running in the background in our app. 


 
 ### Optional
Check out [this exercise](https://github.com/gSchool/ngshop) to practice more with services and dependency injection.