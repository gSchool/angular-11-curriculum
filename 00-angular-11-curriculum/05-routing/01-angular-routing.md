# Client-side routing with Angular

In unit 01, we included a basic Angular router in our app to navigate to the Flights page. Here will we take a deeper dive into the Angular router and build and app that can navigate to several pages using the Angular router.  


Routing allows websites to navigate between multiple full-screen views via navigation links. Angular routing borrows from the same model as browser navigation, by assigning each view its own url, then redirecting users to those urls when the relevant link or navigation button is clicked.  Configuring your site to use front-end routing dramatically decreases the time it takes to navigate from view to view, improving your site's UX significantly.  Nobody likes waiting for every link to load!  This makes client-side routing an essential part of modern single page applications.

Routers work by using paths to control which component is displayed in the view. Components will render within `<router-outlet>` to the main app template.

In this lesson, we'll add client-side routing to our chefs CRUD app.  We'll add a navigation bar with two buttons, "Chef List" and "Add Chef".  The Chef List button will render *only* the list of chefs in our data model, and the Add Chef button will render *only* the form used to add chefs. There are a few things we'll need to take care of:

- [ ] Pull out the `ngFor` portion of `app.component.html` into a new ProfileList component.
- [ ] Configure the Router module in app.module.ts
- [ ] Define and configure our route urls in `app-routing.module.ts`.
- [ ] Add a Router Outlet to the main app template.
- [ ] add navigation links to `app.component.html`

## Refactoring the code

Before we can configure the router properly, we need to alter the structure of our components slightly.  Currently, we're rendering the list of profiles in the App component.  However, this structure will not allow us to render the form and the profile list separately.  We'll have to make a `ProfileList` component if we want to achieve this.  

**QUESTION** What is the Angular CLI command we should use to generate this component?  If you're unsure, go back to *5.3: Building a Basic Form* and take a look at how we generated the form component.  Then, try applying this to create a `ProfileList`.

Once you've generated the new component, go ahead and add the profile list syntax from `app.component.html` to `profile-list.component.html`.  It should look familiar:

```
<app-profile
  *ngFor="let chef of chefs"
  [style.font-weight]="selection === chef.name ? 'bold' : ''"
  [name]="chef.name"
  [email]="chef.email"
  (profileSelected)="handleProfileClick($event)"
></app-profile>
```

Remember to delete this code from `app.component.html`.

## Configuring the Router module and defining the routes

Long ago when we first generated our project, we elected to add Angular routing to our project.  This generated a file called `app-routing.module.ts`.  This module is being added to our main module via the `@NgModule` decorator in the `app.module.ts` file.

**NOTE** the routing module is added to the `imports` array.  remember, **imports** is for modules, **declarations** is for components, and **providers** is for services.

Now, we can open up `app-routing.module.ts` and define some routes!

In that module, you'll find an empty `routes` array.  This is where we'll add our route configuration.  Each different route is defined in a separate object in this array, and you can read more about what these objects can contain in [the documentation](https://angular.io/api/router/Route).  For now, we'll focus on a basic setup.  Go ahead and add a default route, `''`, and an `'add-chef'` route, like so:

```
const routes: Routes = [
  { path: '', component: ProfileListComponent },
  { path: 'add-chef', component: AddChefFormComponent }
];
```

This specifies that the  view rendered by the router as the home screen ('/') is `ProfileListComponent`, but when the Location bar ends with '/add-chef', the `AddChefFormComponent` will be displayed instead.  Before we can see this in action, however, there are a few more tasks to take care of.  

## Adding `<router-outlet>`

We've specified the router's behavior in `app-routing.module.ts`, but Angular's router still doesn't know where to render the appropriate component!  Luckily, adding this is pretty straightforward-- Angular's routing module comes with a pre-built component, RouterOutlet, which we have access to now that we've imported that module.  So, all we'll need to do is add it to the `app.component.html`:

```
<h1>Chefs</h1>
<div>
  <router-outlet></router-outlet>
</div>
```

Now, when you load up the app, you should see the `ProfileListComponent` rendered.  Let's test the router!  In the Location bar, type 'add-chef' after the trailing slash.  You should see the `ProfileListComponent` disappear and the `AddChefFormComponent` appear.  

## Add the navigation links to the app component.

Obviously, we don't want users to have to type the appropriate route into the location bar when they want to navigate the site.  Let's add a few buttons to the site so our users can navigate with ease!  

Recall that Angular's design philosophy involves extending HTML via built-in and custom directives.  In keeping with this, Angular's Routing module comes with a built-in `routerLink` directive which may be added to `<a>` tags.  This directive is similar to the `href` attribute from vanilla HTML, but instead of sending an HTTP request for a new page from a server-side router, the `routerLink` directive will *only* alter the Location bar, triggering the Angular router but not a network request.

Let's take a look at how this works.  In your `app.component.html`, go ahead and add some nav content:

```
<h1>Chefs</h1>
<div>
  <nav>
    <a routerLink=''>Chefs List</a>
    <a routerLink='add-chef'>add-chef</a>
  </nav>
  <router-outlet></router-outlet>
</div>
```

Two buttons should appear.  Clicking them should allow you to navigate your Angular app.

## Extra Practice

Check out [this exercise](https://github.com/gSchool/ngforms) to practice more with Angular forms and routing.