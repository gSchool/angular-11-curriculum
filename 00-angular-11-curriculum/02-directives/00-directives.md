# Directives

In [this video](https://drive.google.com/file/d/1Cac-KxqgP1tcf5Qnb21sSgcKZX66rY81/view) in the 
[lesson on iteration](../01-http/04-iterating-over-objects.md), we talked about *structural directives*.  

You may recall this construct, where _flights_ is an array of objects, and we use an *ngFor* structral directive to loop through the flights: 

```
<div *ngFor="let flight of flights">
    {{flight.origin}}, {{flight.destination}}, {{flight.nonstop}}
</div>

```

We have been using the term *structural directive*, but what does this really mean ?


A directive provides instructions that tell templates how to transform the DOM.  Think of them as custom extensions to HTML syntax.  In other words, *anything you write in a template that isn't vanilla HTML or data-binding syntax is a directive.* Of course, we've already seen one such extension-- the component:

```
<div>
  <app-profile
    [style.font-weight]="selection === 'Cat Cora' ? 'bold' : ''"
    [name]="'Cat Cora'"
    [email]="'cora@foodnetwork.com'"
    (profileSelected)="handleProfileClick($event)"
  ></app-profile>
  <app-profile
    [style.font-weight]="selection === 'Masaharu Morimoto' ? 'bold' : ''"
    [name]="'Masaharu Morimoto'"
    [email]="'morimoto@foodnetwork.com'"
    (profileSelected)="handleProfileClick($event)"
  ></app-profile>
  <app-profile
    [style.font-weight]="selection === 'Bobby Flay' ? 'bold' : ''"
    [name]="'Bobby Flay'"
    [email]="'flay@foodnetwork.com'"
    (profileSelected)="handleProfileClick($event)"
  ></app-profile>
</div>
```

`<app-profile>` is an extension **we** made to HTML. **We** defined what should be rendered when the HTML parser encounters `<app-profile>` (in `profile.component.html`), and **we** defined the behavior it should have (in `profile.component.ts`).  But this is only one of several types of directive.

| Directive Type  | Example   |
|---	            |---        |
| [Structural Directive](https://angular.io/guide/structural-directives) | *ngFor="let item of items"<br> *ngIf="condition" |
| [Attribute Directive](https://angular.io/guide/attribute-directives#directives-overview)  | [(ngModel)]=”property” <br> [customAttr]=”value”<br> `<p customAttr></p>` |
| Component | ProfileComponent <br> |

Angular comes with a number of useful built-in directives, but it's also possible to define your own (using the [Directive decorator](https://angular.io/api/core/Directive)).  Here's a list of a few of the most common Angular directives:

| directive | Used for: |
|---        |--- |
| ngFor     | Repeating items based on data in the component.  |
| ngIf      | hiding or showing items based on data in the component|
| ngStyle   | Defining styles dynamically |

In fact, our current App component template is becoming quite large and repetitive.  Let's use  structural directives to help improve our code.

- [ ] Move profile data from the template into the App component.
- [ ] Use ngFor to display one profile for each student.

## Setting up the data

Right now, all the data needed for our chefs' profiles is stored in the template.  This is a problem for a few reasons.  First, it's relatively inaccessible-- it can be read by the Profile component and not much else.  Second, the role of a template is to specify information about the application's view, *not* contain the underlying data.  We'll have to move it.  In the next lesson, we'll look at services, which are used for distributing data through an application, but for now we'll store this information in the component itself:

```
export class AppComponent {
  ...
  chefs: Object[] = [
    {
        "name": "Bobby Flay",
        "email": "flay@foodnetwork.com"
    },
    {
        "name": "Masaharu Morimoto",
        "email": "morimoto@foodnetwork.com"
    },
    {
        "name": "Cat Cora",
        "email": "cora@foodnetwork.com"
    }
  ]
  ...
}
```

Now we're ready to refactor our template!

## ngFor

`ngFor` is a **structural directive**  which iterates over a list of items, creating and rendering a DOM element for each one.  We currently have three profile components hard-coded into `app.component.html.`, but now that we have an array in our component containing the chef data, we can render the profile components dynamically. That way, if chefs are added or removed, our list of profiles will reflect that.  Let's swap out the current contents of `app.component.html` for something like the following:

```
// app.component.html

<div>
  <app-profile
    *ngFor="let chef of chefs"
    [style.font-weight]="selection === chef.name ?   'bold' : ''"
    [name]="chef.name"
    [email]="chef.email"
    (profileSelected)="handleProfileClick($event)"
  ></app-profile>
</div>
```

Take a look at what we wrote:  the value of ngFor is reminiscent of [JavaScript's for...of loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of).  This makes sense, as it's doing something very similar to a for...of loop.  Every time Angular renders the app component, the ngFor directive will loop over the items in the `chefs` list we made a moment ago.  For each item in that list, it will create and render a new profile component, passing the current chef's details (`chef.name` and `chef.email`) in turn.

## ngStyle

Let's take a look at an attribute directive.  In this case, we'll use `ngStyle` to remove the style binding in our component.  This will make our template more readable, and properly separates concerns between the template (formatting and displaying) and the component (component logic).  To do this, we'll need to add a few methods and properties to the component.  First, we'll add a `style` property:

```
  style: object = {
    'color': 'black',
  }
```

This field will hold all of the **dynamic** style rules for this component (in this case, that's all the style rules that change when we select the component).

Next, let's add a method that allows us to toggle this color from black to red.

```
  toggleColor() {
    if(this.style['color'] === 'black') 
      this.style['color'] = 'red'
    else 
      this.style['color'] = 'black'
  }
```
  Now we can invoke that method in our click handler: 

```
  select() {
    this.toggleColor();
  }
```

  Finally, let's write a getter for this style property:

```
  getStyle() {
    return this.style;
  }
```

We're finally prepared!  Let's head over to the template.  Here, we can add the `ngStyle` attribute directive to our component:

```
<div 
  [ngStyle]="getStyle()"
  (click)="select()"
  ...
>
  ...
</div>
```

Notice that we must use the property-binding syntax `[]` to bind this directive to the component.

This improvement makes our template much cleaner, and means that we can design more elaborate style interactions and mutations within the component itself.  Congratulations!  You've used your first structural and attribute directives!

Use this interactive playground on StackBlitz to explore *attribute directives* that modify HTML :

https://stackblitz.com/edit/angular-ivy-pwq2hj?file=src%2Fapp%2Fapp.component.html

*Assignment*: 

Create your own Angular app on StackBlitz that explores attribute directives. 

You should use at least two of the following attribute directives: 

* NgSwitch
* NgStyle
* NgClass


### !challenge

* type: project
* id: DIRCHEMA-EC86-4015-9AA8-28dka23kdsdd
* title: Attribute directives
* topics: Directives  
##### !question
Paste the URL of your Stackblitz attribute directives demo
##### !end-question

 

##### !answer
* Answer
##### !end-answer

<!-- other optional sections -->
<!-- !hint - !end-hint (markdown, users can see after a failed attempt) -->
<!-- !rubric - !end-rubric (markdown, instructors can see while scoring a checkpoint) -->
##### !explanation

Thank you for your submission

##### !end-explanation

### !end-challenge


