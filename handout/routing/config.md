# Configuring Routes #

## Base URL Tag ##

The Base URL tag must be set within the `<head>` tag of index.html:

```html
<base href="/">
```

> In the demos we use a script tag to set the base tag. In a real application it must be set as above.

## Route Definition Object ##

The `RouteConfig` type is an array of routes that defines the routing for the application. This is where we can set up the expected paths, the components we want to use and what we want our application to understand them as. 

Each route can have different attributes; some of the common attributes are:

* _path_ - URL to be shown in the browser when application is on the specific route
* _component_ - component to be rendered when the application is on the specific route
* _redirectTo_ - redirect route if needed; each route can have either component or redirect attribute defined in the route (covered later in this chapter)
* _pathMatch_ - optional property that defaults to 'prefix'; determines whether to match full URLs or just the beginning. When defining a route with empty path string set pathMatch to 'full', otherwise it will match all paths.
* _children_ - array of route definitions objects representing the child routes of this route (covered later in this chapter).

To use `RouteConfig`, create a RouteConfig array which contains [Route Definition Object](#route-definition-object)s.

Below is the sample RouteConfig array definition:

```javascript
const routes: RouterConfig = [
  { path: 'component-one', component: ComponentOne },
  { path: 'component-two', component: ComponentTwo }
];
```

[See RouteConfig definition](https://angular.io/docs/ts/latest/api/router/index/RouterConfig-type-alias.html)

## provideRouter ##

`provideRouter` takes the `RouteConfig` array as an argument and returns the providers necessary for routing.

The providers returned by `provideRouter` *must* be provided when bootstrapping the application to register the routes. In the bootstrap file:

```javascript
import { provideRouter, RouterConfig } from '@angular/router';

const routes: RouterConfig = [
  { path: 'component-one', component: ComponentOne },
  { path: 'component-two', component: ComponentTwo }
];

bootstrap(AppComponent, [
  provideRouter(routes)
]);
```

