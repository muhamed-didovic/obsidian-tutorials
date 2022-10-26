
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
	<body>

		<!-- 
		- Is x-data mandatory for events?
		- there is a shorter version or shorthand for for 'x-on' directive, which is the '@' symbol like in vue.js 
		- example wile holding shift button or key
		- '$el' is DOM element that you are working on
		- 'keyup.enter' or 'keydown.shift' are modifiers that can be added to directives
		-->
		<form x-data x-on:submit.prevent="console.log('submitted')">
			<textarea
				cols="30"
				rows="10"
				x-data="{ shiftHeld:false }"
				x-on:keydown.shift="shiftHeld = true"
				x-on:keyup.shift="shiftHeld = false"
				x-on:keyup.enter="if (!shiftHeld) { $el.closest('form').dispatchEvent(new Event('submit')) }"
			></textarea>
		</form>
	</body>
</html>
```

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
	<body>
		<style>
			.box {
				height: 200px;
				width: 200px;
				background-color: steelblue;
			}
		</style>
		<!-- Example -->

		<div x-data="{ open: false }">
			<button x-on:click="open = true">Open</button>
			<div x-show="open" x-on:click.outside="open = false" class="box">
				Menu Content
			</div>
		</div>
	</body>
</html>
```