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
	</style>

	<body>
		<!-- 
		- List of people, represented by checkboxes which we can select and then when it is selected, their styling changes 
		- we used here also x-for loop to iterate over people array, also when x-for loop is used we need to use template element or tag
		- notice how x-bind is used with 'value' of input and even 'id' of input, also we have selected variable, which holds all people who are selected, later we use that  to apply class conditionally with includes method, here is important to notice that in people array of objects ID is integer, but in selected variable those numbers are represented as string so author uses casting  to cast number to string when we check what we have in selected variable with: x-bind:class="{'bold': selected.includes(person.id.toString())}"
		- in order to even more simplify casting or not to use it with toString method, in Alpine there are so called modifier which is basically casting values, so in our example we use number modifier like: x-model.number="selected" for input text model attribute 
		-->
		<div
			x-data="{ 
			
			selected: [],
			people: [
				{id: 1, name:'Alex'},
				{id: 2, name:'Billy'},
				{id: 3, name:'Mabel'}
			] 
	}"
		>
			<template x-for="person in people">
				<div>
					<input
						type="checkbox"
						x-bind:value="person.id"
						x-bind:id="`person_${person.id}`"
						x-model.number="selected"
					/>
					<span
						x-text="person.name"
						x-bind:class="{'bold': selected.includes(person.id)}"
					></span>
				</div>
			</template>
			<!--DEBUG-->
			<span x-text="selected"></span>
		</div>
	</body>
</html>
```

Progress bar example:
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

		.progress {
			height: 10px;
			width: 300px;
			background-color: #ccc;
		}

		.progress-inner {
			height: 10px;
			background-color: slategray;
		}
	</style>

	<body>
		<!-- 
		- author builds a custom progress bar, here is introduces init method which is part of the life cycle of Alpine
		 -->
		<div
			x-data="{ 
			progress: 0,
			
			increment () {
				this.progress = this.progress + 10
			},
			init () {
				let interval = setInterval( () => {
					if(this.progress >= 100){
						clearInterval(interval)
					}
					
					this.increment()
				}, 100)
			}
		 }"
		>
			<div class="progress">
				<div class="progress-inner" x-bind:style="`width: ${progress}%;`"></div>
			</div>
			<button x-on:click="increment">Increment</button>
		</div>
	</body>
</html>
```