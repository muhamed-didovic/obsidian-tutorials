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
 
</head>  
<body>  

	<p> Without Spruce:</p>
	<div x-data="{
		count: 0
	}">
		<button @click="count--">Decrement</button>
		<div x-text="count">0</div>
		<button @click="count++">Increment</button>
	</div>


	<p> With Spruce:</p>
	<div x-data x-subscribe>
		<!--
			to access store we use $store global variable or object
		-->
	    <button @click="$store.counter.count--">Decrement</button>
	</div>

	<div x-data x-subscribe>
	    <p x-text="$store.counter.count"></p>
	</div>
	
	<div x-data x-subscribe>
	    <button @click="$store.counter.count++">Increment</button>
	</div>

	<script>
		/*
		- 'counter' is the name of the store
		- the second argument of store method is object which holds our state
		- x-subscribe directive or attribute must be added to DOM elements or global state, basically Apline components are not aware of Spruce until we add the mentioned directive
		- x-subscribe directive goes with x-data directive hand in hand
		*/
		Spruce.store('counter', {
		    count: 0
		});
	</script>
</body>  
</html>
```

Learned in this lesson:
1. created a global store
2. subscribed to store
3.  way to access and change global state or store