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
	    <button @click="$store.counter.count--">Decrement</button>
	</div>

	<div x-data x-subscribe>
	    <p x-text="$store.counter.count"></p>
	</div>
	
	<div x-data x-subscribe>
	    <button @click="$store.counter.count++">Increment</button>
	</div>

	<script>
		Spruce.store('counter', {
		    count: 0
		});

		/*
		- watch method takes two arguments
		- first argument is dot representation of our state, in our case it is counter.count
		- second argument is callback which receives two values old and new value
		*/
		Sprice.watch('counter.count' (old, next) => {
			console.log(`${old} - ${next}`)
		})
	</script>
</body>  
</html>
```

Learned in this lesson:
1. watch method and arguments
2. how to watch for changes and check the values