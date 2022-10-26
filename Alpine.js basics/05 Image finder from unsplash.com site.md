Build a form that searches image from unsplash.com and returns it
```html
<!doctype html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport"  
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">  
    <meta http-equiv="X-UA-Compatible" content="ie=edge">  
    <title>Document</title>  
  
    <script src="https://unpkg.com/alpinejs" defer></script>  
</head>  
<body>  
	<div

		x-data="{
			query: '',
			image: '',
			getImage () {
				this.image = `https://source.unsplash.com/1600x900/?${this.query}`
			}
		}"
	>				
		
		<form x-on:submit.prevent="getImage">
		
			<input type="text" x-model="query" />
		
			<button type="submit">Search</button>
		
		</form>
		
		<div x-show="image">
		
			<img x-bind:src="image" style="width: 300px" />
		
		</div>
		
	</div>
</body>  
</html>
```

Notes:
- x-bind:src attribute/component is used for image so that Alpine.js will handle the rest 
- x-show component is used to display only if it is not empty
- also look how 'wrapper' is done, which holds all the data