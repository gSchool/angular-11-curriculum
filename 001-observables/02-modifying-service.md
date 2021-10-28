# Flight Data Using Observables

Currently, the flights service is providing data in an entirely *synchronous* manner.  This will work for mock data, but is totally inadequate for a production application pulling data from the web in an asynchronous manner.  We'd like provide a way

Let's implement this in our service!  We'll need to:

- [ ] Create an Observable containing our flight data in `FlightService`
- [ ] Subscribe to that Observable in our component

## Creating the Observable

First, we need to import the relevant classes and functions from the ReactiveX library.  Angular installed ReactiveX automatically when we created our project, so all we need to do is import them:

```
import { Observable, of } from 'rxjs';
```

* **Observable** is the class we'll be using for typing purposes.
* **of** is a static method that [creates an observable from an array](http://reactivex.io/rxjs/class/es6/Observable.js~Observable.html#static-method-of).

Now we've got to create an observable from our flight data.  Recall that our Flight class looks something like this:

```
getFlights():Flight[] {
  return flights;
}
```

All it does is return a copy of the `flights` array imported into the service from `flight.ts`.  Since this is the only access method for our flight data, we can alter this method to return an Observable instead.  Let's use `of` to achieve this.

```
getFlights():Observable<Flight[]> {
  return of(flights);
}
```

**NOTE** We need to specify to Typescript that we're returning an *Observable containing Flights* now.  That's why we've changed the return type from `Flight[]` to `Observable<Flight[]>`

## Subscribing to the Observable

Now, let's update the component so that it subscribes to the observable returned by `FlightService.getFlights()`.  Previously, we wrapped this call in another, similarly-named `getFlights()` method:

```
getFlights(): void {
  this.flights = this.flightSerivce.getFlights();
}
```

This assumes that the return value from `flightsService.getFlights` is an array.  However, we just modified that method to return an Observable!  So, we'll have to use the `subscribe` method on that Observable to update the value of `this.flights` every time new data is emitted by the observable.

```
getFlights(): void {
  this.flightsService.getFlights().subscribe(flights => this.flights = flights);
}
```

That's it!  

## Exercise

Now, get some [practice connecting a server to a REST API](https://github.com/jtklier/httpClient-demo)

## Advanced Content

Take some time to [work through this awesome ReactiveX tutorial!](http://reactivex.io/learnrx/)

**NOTE** The first 25 or so of these exercises are actually practice for functional programming and higher-order functions.  You can skip them if you want, but I highly encourage you to work through them.