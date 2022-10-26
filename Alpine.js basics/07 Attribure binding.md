
Bind any attribute value based on expression:
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
	<!-- 
	- Adding class attribute conditionally based on condition
	- format is: x-bind:[name-of-attribute] 
	- in our example, we bind the class conditionally; the object  contains key value which will be added to class and value of the object is expression that needs to be evaluated to be true/false
	- in our example, we already have a class, so our conditionally class will be appended to previous classes if they are any
	-->
	<div x-data>
	
		<span class="blue" x-bind:class="{ 'bold': true }">
			Am I bold?
		</span>
	</div>  
  
</body>  
</html>
```

Toggle adding of class:
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
	<div x-data="{ selected: false }">

		<span class="blue" x-bind:class="{ 'bold': selected }">
		Am I bold?
		</span>
		
		<button x-on:click="selected = !selected">
			Make it Bold
		</button>
		
	</div> 
  
</body>  
</html>
```

Form disabled attribute:
```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta http-equiv="X-UA-Compatible" content="IE=edge" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Document</title>

		<script src="https://unpkg.com/alpinejs" defer></script>
	</head>
	<style>
		.bold {
			font-weight: bold;
		}
		.blue {
			color: blue;
		}
	</style>
	<body>
		<!-- Button should be enabled when there is some text in input -->
		<form x-data="{ name: '' }" x-on:submit.prevent="alert(`Hey ${name}`)">
			<input type="text" x-model="name" />
			<button type="submit" x-bind:disabled="name === '' ">Lets Go</button>
		</form>
	</body>
</html>
```

Style attribute like progress bar:
```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta http-equiv="X-UA-Compatible" content="IE=edge" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Document</title>

		<script src="https://unpkg.com/alpinejs" defer></script>
	</head>
	<style>
		.bold {
			font-weight: bold;
		}
		.blue {
			color: blue;
		}
	</style>
	<body>
		
		<!-- Example 4 -->
		<div x-data="{ progress: 0 }">
			<progress max="100" x-bind:value="progress">
				<span x-text="`${progress}%`"></span>
			</progress>
			<button x-on:click="progress = progress + 5">Increment</button>
		</div>
	</body>
</html>
```