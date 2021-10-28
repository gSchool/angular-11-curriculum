# Angular forms
<!--
  Describe: https://docs.google.com/presentation/d/1yJiei-PKTcQQ9v0B48Yl0Fvvt9KHgJfu2NVoJupMfnM/edit#slide=id.g57baba6955_1_14
  Describe: https://docs.google.com/presentation/d/1yJiei-PKTcQQ9v0B48Yl0Fvvt9KHgJfu2NVoJupMfnM/edit#slide=id.g57baba6955_1_21
-->

Forms are one of the most common features of web applications.  They allow users to input needed data in an orderly and structured way.  Angular provides an interface for designing interactive forms with dynamic validation built around [forms in HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms). Forms in Angular are written either as "reactive" or "template-driven", both of which we will be looking at in the coming lessons.  The difference, according to [the Angular documentation](https://angular.io/guide/forms-overview), can be summarized as follows:

* **Reactive forms** are more robust: they're more scalable, reusable, and testable. Well-written reactive forms use observables to manage asynchronicity and focus on clean, functional code to manage the form logic.  If forms are a key part of your application, or you're already using reactive patterns for building your application, use reactive forms.
* **Template-driven forms** are useful for adding a simple form to an app, such as an email list signup form. They're easy to add to an app, but they don't scale as well as reactive forms. If you have very basic form requirements and logic that can be managed solely in the template, use template-driven forms.

Both the reactive and template-driven form patterns share a common set of "building blocks."  One of these building blocks is the `FormControl` class, which is used to track the values and validation of an individual input.  `FormControl` instances are generally collected into a `FormGroup`, which is responsible for tracking all the input values for a particular form.  We'll look more at how this works in the next lesson.
