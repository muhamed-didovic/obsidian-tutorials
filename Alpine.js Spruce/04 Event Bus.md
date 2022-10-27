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

	<!-- Important notes:
	- we need to add window modifier so it listens for global event not on component
	- we get $event argument or variable from event
	-->	
	<div 
		x-data
		x-subscribe
		@spruce:count-changed.window="console.log($event.detail)"
	>
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
		- emit method, emits the event and it takes two arguments
		- first argument name of the event
		- second argument data to send
		*/
		Spruce.watch('counter.count' (old, next) => {
			console.log(`${old} - ${next}`)
			Spruce.emit('count-changed', {old, next})
		})

		//listener for an event
		//two arguments: name of the event and data that it receives 
		Spruce.on('count-changed', (data) => {
			console.log(data)
		})
	</script>
</body>  
</html>
```

Learned in this lesson:
1. listen and emit events
2. Listener data: ![[Pasted image 20221026162512.png]]
3. event on component (console.log($event)):![[Pasted image 20221026163449.png]]