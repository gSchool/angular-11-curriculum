# Building a Basic Form

In this lesson we'll walk through the process of creating a basic reactive form in Angular.  From there, we will look at adding validation.  Later on we'll discuss template-driven forms in more detail.  For now, here are the tasks we'll need to take care of:

- [ ] Create a form component
- [ ] Add an input to the template
- [ ] Instantiate a new `FormControl` in the component
- [ ] set up two-way data binding between the input in the template and the `FormControl` instance in the form component.
- [ ] Add a few more inputs to the template, and swap out `FormControl` for a `FormGroup`.

Let's start by adding a new component to our project:

```
ng g component AddChefForm
```

Now, we can add this to the top of our  the contents of our `app.component.html` with our profile form component.  It should look something like this:

```
<div>
  <app-add-chef-form></app-add-chef-form>
  <app-profile
    ...
  ></app-profile>
</div>
```

At this point, the message "add-chef-form works!" should be at the top of the screen.

## A single input

We'll start by adding a single text input to our component.  Doing this is as easy as replacing the contents of `add-chef-form.component.html` with:

```
<label>
  First name:
  <input type="text">
</label>
```

Next, let's add a `FormControl` to the component so that our template has something to bind to.  Head back over to `add-chef-form.component.ts` and import `FormControl` from '@angular/forms'.  Then, create a new `FormControl` instance as a member of the profile form component:

```
export class AddChefFormComponent implements OnInit {
  firstName: FormControl = new FormControl('');
  ...
}
```

Now that we have our input defined in the template and our controller defined in our component, it's time to bind them together.  We'll do this using the `formControl` directive, which we bind in the template like so:  

```
<label>
  Name:
  <input [formControl]="firstName" type="text">
</label>
```

Now, we're always able to access the input's value and validation status via `this.firstName`.  

Take a look at the Chrome console.  You should now see an error stating that you "Can't bind to 'formControl' since it isn't a known property of 'input'."  This error is appearing because the form control directive is part of a separate Angular module which we have not yet imported into our project.  To import the required modules, head over to `app.module.ts` and import `FormsModule` and `ReactiveFormsModule` from '@angular/forms'.  Then, inside the `@NgModule` decorator, import them:

```
imports: [
  BrowserModule,
  FormsModule,
  ReactiveFormsModule
]
```

Head back over to your application.  The error should be gone and your form should be back.  Congratulations!  We have achieved data-binding.

**NOTE** If you have Augury installed, you can open up the augury tab in the Chrome developer tools and click `AddChefFormComponent`.  You should see the `value` field change in real-time as you type.

## Multiple inputs with `FormGroup`

Forms rarely involve only a single input.  Let's take a look at the way Angular manages forms with multiple inputs using `FormGroup`.

First, let's add another input to our template in `profile-form.component.html`, and we'll organize them nicely by wrapping them in `<form>` tags:  

```
<form>
  <label>
    Name:
    <input type="text">
  </label>
  <label>
    Email:
    <input type="text">
  </label>
<form>
```

Notice that we've removed the `[formControl]` directive from our input.  We'll come back to the template in a moment when it's time to bind our data, but first let's take care of the component.  In `add-chef-form.component.ts`, let's add `FormGroup` to our imports from '@angular/forms'.  Then, we can swap out `firstName` property for a more general `profileFormGroup`:

```
export class AddChefFormComponent implements OnInit {
  addChefFormGroup: FormGroup = new FormGroup({
    name: new FormControl(''),
    email: new FormControl('')
  });
  ...
}
```

Notice the way we instantiate our new form group object-- by passing it an object which defines the *shape* of our form data.  In this case, because our form has two inputs, we create two new `FormControl`s in our object, one for each input.  Remember:  

* `FormControl` is a class which manages an individual input's state.
* `FormGroup` is a class which collects all the individual inputs within a given form, and provides structured access to their  `FormControls`.

Now that our form group is set up, let's head back to the template and handle our data binding.  We'll make use of two new directives, `formGroup` and `formControlName` to do this:

```
<form [formGroup]="addChefFormGroup">
  <label>
    Name:
    <input formControlName="name" type="text">
  </label>
  <label>
    Email:
    <input formControlName="email" type="text">
  </label>
<form>
```

Observe what each of these directives is doing:  `[formGroup]` is added to the `<form>` tag and binds that particular form with the `profileFormGroup` property which we just declared in the component.  Within the form, `formControlName` is added to each input.  This binds that input to the form control of the specified name in the configuration object we passed into our `FormGroup`.

## Submitting the form

There's just one small problem with our form, as it is:  There's no way to submit it!  To allow users to submit their form, we'll have to add a submit button:

```
<label>
  <input type="submit">
</label>
```

The default behavior for an HTML submit button is to send a POST request to the server with the form data.  It will then render the response, causing a page refresh.  Since we're building an SPA, we don't want to refresh the page at this point in time.  Rather, we want to specify a custom function to run when the submit button is clicked.  We can do this using event binding to the custom `ngSubmit` event:

```
<form [formGroup]="addChefFormGroup" (ngSubmit)="addChef()">
  ...
```

Now, we need to add an `addChef` method to the component.  This will simply delegate the process of adding data to the  `ChefsService` (remember, services are responsible for CRUD operations on the data model, *not* components!).  

```
addChef() {
  const chef = {
    name: this.addChefFormGroup.controls.name.value,
    email: this.addChefFormGroup.controls.email.value
  }
  this.chefsService.add(chef)
}
```

Now, let's hop into `chefs.service.ts` and write that `add` method:

```
add(chef: Chef) {
  chefs.push(chef)
}
```

Congratulations!  You've completed your first reactive form with Angular.  As before, if you're using Augury, you can use it to observe the data as it updates in our service.