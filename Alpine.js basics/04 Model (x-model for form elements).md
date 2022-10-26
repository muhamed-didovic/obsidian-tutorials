
Data binding, like v-model in Vue.js in Alpine.js we have x-model

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
	<div x-data="{name: ''}">  
		<input type="text" x-model="name" />
		<span x-text="name"></span>
		<span x-text="name.length"></span>
	</div>  
  
</body>  
</html>
```

Form:
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
	<form x-data="{name: ''}" x-on:submit.prevent="console.log(name)">  
		<input type="text" x-model="name" />
		<button type="submit">Submit</button>
	</form>  
  
</body>  
</html>
```

Form (preventDefault inside):
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
	<form x-data="{name: ''}" x-on:submit="$event.preventDefault();console.log(name)">  
		<input type="text" x-model="name" />
		<button type="submit">Submit</button>
	</form>  
  
</body>  
</html>
```

Two way data binding:
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
			name: '',
			makeNameUppercase() {
				this.name = this.name.toUpperCase()
			}
		}"
	>  
		<input type="text" x-model="name" />
		<span x-text="name"></span>
		<button x-on:click="makeNameUppercase">Uppercase</button>
	</div> 
  
</body>  
</html>
```