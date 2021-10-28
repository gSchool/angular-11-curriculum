# Observables

Angular uses the Observable pattern from the [ReactiveX library](http://reactivex.io/) to manage asynchronous data flow.  This allows Angular services to adopt a 'publication/subscription' model, and also provides a number of convenient utility methods for asynchronous data management.

In this lesson, we'll add an Observable to the `ChefsService` we built in a previous lesson.  This will allow our components to consume changes in the data as they arise!

## The Observable pattern

An Observable might be thought of as an "asynchronous array"-- That is, an array in which new items will be added over time.  Each Observable can be subscribed to, and will publish new data to all of its subscribers as those data are added.  

Without knowing it, you've already been using Observables!  Recall that when we covered event binding, we had to import an `EventEmitter` class from `@angular/core`.  *the EventEmitter class uses an Observable under the hood.*  The observer pattern actually involves a number of different classes:

* [Observables](http://reactivex.io/documentation/observable.html)
* Observers
* [Subjects](http://reactivex.io/documentation/subject.html)

...And many more!

ReactiveX is a very large library, and there's quite a lot to learn.  This lesson will focus on the details necessary to add an observable to our Angular app.  Please work through this material first, as it's most directly relevant.  However, once your finished, feel free to [dive into the deep end](http://reactivex.io/tutorials.html).