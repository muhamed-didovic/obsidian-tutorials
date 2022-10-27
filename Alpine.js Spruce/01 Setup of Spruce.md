Spruce is a global state management library for [Alpine.js](https://github.com/alpinejs/alpine). It allows you to share pieces of data (state) between individual components.

## What problem does it solve?[](#what-problem-does-it-solve)

Alpine **does not** have a core way of sharing state between components. Out of the box, you have a few options:

-   1. Use the `$dispatch` helper to send browser events up the DOM and notify other components of state changes.
    

-   2. Use a global object to hold some state and trick Alpine into re-rendering.
    

-   3. Use a "Big" component that holds all of the shared state.
    

These options have some disadvantages though.

-   1. Constantly dispatching browser events can become messy and confusing. You need to keep track of which events are being used on a page and ensure that any changes to those events don't negatively impact other components.
    

-   2. Tricking Alpine into re-rendering can also be risky since all of these APIs are not publically documented and could therefore break in a minor release.
    

-   3. "Big" components can negatively impact performance on a site since Alpine walks the entire DOM tree of a component. Adding an `x-data` attribute to your `<body>` element would mean Alpine needs to walk the entire `<body>` elements DOM tree to find directives (or new components).
    

## How does it solve it?[](#how-does-it-solve-it)

Spruce provides a single API for sharing state and handles the re-rendering process for you. Thanks to Alpine's "magic properties" API, it can hook directly into Alpine's variable resolution and feels like any other magic property that Alpine provides out of the box, such as `$el` or `$dispatch`.

Here are installation link from source: https://spruce.ryangjchandler.co.uk/installation

```html
<!doctype html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport"  
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">  
    <meta http-equiv="X-UA-Compatible" content="ie=edge">  
    <title>Document</title>  
	
	<script src="https://cdn.jsdelivr.net/npm/@ryangjchandler/spruce@2.x.x/dist/spruce.umd.js"></script>
    <script src="https://cdn.jsdelivr.net/gh/alpinejs/alpine@v2.x.x/dist/alpine.min.js" defer></script>
    <style>

		.bold {
			font-weight: bold;
		}
		
		.blue {
			color: blue;
		}
	
	</style>  
</head>  
<body>  
	<div x-data>
    <div x-show="$store.modal.open === 'login'">
        <p>
            This "login" modal isn't built with a11y in mind, don't actually use it
        </p>
    </div>
</div>

<div x-data>
    <div x-show="$store.modal.open === 'register'">
        <p>
            This "register" modal isn't built with a11y in mind, don't actually use it
        </p>
    </div>
</div>

<div x-data>
    <select x-model="$store.modal.open">
        <option value="login" selected>login</option>
        <option value="register">register</option>
    </select>
</div>

<script>
window.Spruce.store('modal', {
    open: 'login',
});
</script>
</body>  
</html>
```