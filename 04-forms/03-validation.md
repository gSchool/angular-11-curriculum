# Form Validation

Form validation is the process of ensuring that all data entered into a form is of the correct shape.  For instance, an email has a very specific pattern to it: a handle, the @ symbol, and a domain name.  We can use this knowledge to check whether a user has entered an email address into our "email" input.

Writing this code for ourselves from scratch is tedious.  Luckily, Angular provides a system for validation forms: the `Validator` class.

Let’s set up some basic validation on our example app. To do this, we'll have to do the following:

- [ ] Add Validators to our `FormControl`s.
- [ ] Add some user-facing error messages to our template.
- [ ] Bind the error messages to the validation status of each input.

## Adding the Validators

We'll begin by adding our validators.  We'll need to import the `Validators` class from `@angular/forms`.  This gives us access to a number of pre-built methods for validating our inputs:

* `Validators.required`
* `Validators.minLength`
* `Validators.maxLength`
* `Validators.email`
* `Validators.pattern`

You can read more on Validators [here](https://angular.io/api/forms/Validators).

Perhaps the most basic form of form validation is simply requiring the user to provide *something* as input.  This is what the `Validators.required` method does.  Let's add this validator to each input on our form, by passing it into each `FormControl` constructor call like so:

```
name: new FormControl('', [
  Validators.required
]),
email: new FormControl('',[
  Validators.required
])
```

Notice that each validator is wrapped in an array.  This syntax will allow us to add additional validators wherever we choose.  For instance, we might add the email validator to our email input:  

```
email: new FormControl('',[
  Validators.required,
  Validators.email
])
```

**CHALLENGE** How would you validate the name input to only validate strings beginning with capital letters?

## Editing the template and Binding the Data

Let's take a moment to observe our validators in action. Open up Augury, and watch what happens to the values in `profileFormGroup` and its controls.
* Submit the blank form. Observe your console logs. Is it valid?
* Fill in the form and submit. Any differences?
* Is the email field checking for a valid email?
* Is the password field checking for valid password?

Recall that each `FormControl` is responsible for the value *and validation status* of exactly one input.  What we should be able to see now is that this is stored in the `status` field.  With that in mind, let's update our template to display some nice error messages to the user if their data is invalid:

```
<form [formGroup]="addChefFormGroup">
    <label>
      First name:
      <input formControlName="name" type="text">
      <div
        *ngIf="addChefFormGroup.controls.email.touched && addChefFormGroup.controls.name.status === 'INVALID'">
          That's not a name!
      </div>
    </label>
    <label>
      Email:
      <input formControlName="email" type="text">
      <div
      *ngIf="addChefFormGroup.controls.email.touched && addChefFormGroup.controls.email.status === 'INVALID'">   
        That's not an email!
      </div>
    </label>
```

And Voila!  We have successfully added validation to our form.

**NOTE** Recall that `FormControl` is responsible for storing the value *and validation status* of an input.  It does this by assigning the string `'VALID'` or `'INVALID'` to the `formControl.status` field.  the `formControl.touched` field tracks whether a user has clicked or tabbed onto the input yet.  We've added this so that the error message doesn't display before the user has even opened the page!