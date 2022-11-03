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

	<div 
		x-data
		x-subscribe
	>
	    <p x-text="$store.counter.count"></p>
	</div>
	
	<div x-data x-subscribe>
	    <button @click="$store.counter.count++">Increment</button>
	</div>

	<button id="increment-2">Increment by 2</button>

	<script>
		Spruce.store('counter', {
		    count: 0
		});

	
		document.querySelector('increment-2').addEventListener('click', () => {
			console.log(Sprice.store('counter'))
			//increment count by 2
			Sprice.store('counter').count += 2
		})
	</script>
</body>  
</html>
```

Learned in this lesson:
1. Spruce allows easy access and management or update or modify of data outside of Alpine
2. console.log(Sprice.store('counter'))![](./assets/Pasted%20image%2020221026164042.png)
