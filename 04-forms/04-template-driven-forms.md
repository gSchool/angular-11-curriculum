# Template-Driven Forms

As the name implies, Template-Driven forms are similar to what you’re already used to with HTML forms.  Unlike reactive forms, template-driven forms pack as much of the logic as possible into the template, using directives to bind data to the component.  This process follows a specific pattern:

1) User inputs data.
2) Form emits the data.
3) FormControl sets the value and emits to valueChanges observable.
4) Subscribers receive new value.
5) The model is updated.
6) The component is updated.

<!-- Describe: https://docs.google.com/presentation/d/1yJiei-PKTcQQ9v0B48Yl0Fvvt9KHgJfu2NVoJupMfnM/edit#slide=id.g57baba6955_1_6 -->

Let’s create a new component SubscribeFormComponent. We’ll use the template approach.

* Create a new component.
* Add it to app.component.html
* Remove <login-form> from app.component.html for now.

Open `subscribe-form.component.ts` and add a single property:
* email (Type string)

```
@Component({ … })
export class SubscribeFormComponent implements OnInit {

  email: string;

  constructor() { }

  ngOnInit() {
  }
}
```

Open `subscribe-form.component.html`
* Add a simple form with email and submit button.

```
<form>
  Email:
 <input type="email" formControlName="email" [(ngModel)]="email" name="email">

  <input type="submit" value="Subscribe">
</form>

<div>
 Current email: {{ email }}
</div>
```

The ngForm directive creates a FormControl instance and binds it to a model.
In this case, the model is SubscribeFormComponent.email
At this stage we need a way to handle the form data in the component.

We can use **template variables** to access the forms properties from the component.
Note the syntax. **Add this variable to our form.**

```
<form #subscribeForm="ngForm">
```

The form is almost ready, but we now need to handle the data. Open `subscribe-form.component.ts`
* Create a new method `addSubscriber()`

```
@Component({ … })
export class SubscribeFormComponent implements OnInit {

 addSubscriber(form) {
   if (form.valid) {
     console.log('Subscription success!', form.value);
   } else {
     console.log('Subscribe FAIL!');
   }
 }
}
```

Finally, add a directive to the form. Open `subscribe-form.component.ts`
* Add ngSubmit directive and pass the variable to the handler
* Add validation properties: required and email handler
* Add a directive to show user message on invalid email entry

```
<form #subscribeForm="ngForm" (ngSubmit)="addSubscriber(subscribeForm)">
  Email:
 <input type="email" formControlName="email" [(ngModel)]="email"
    name="email"
    required email>
 <div *ngIf="subscribeForm.invalid && subscribeForm.dirty">
   Fill in email.
 </div>
```

Test out the form.
* Does it validate the email?
* Can you see the text appear on the page as you type?
* Are the console logs correct for success/failure?

The next exercise is to add a new form to the current application. Review the instructions [here](https://github.com/gSchool/ngforms).