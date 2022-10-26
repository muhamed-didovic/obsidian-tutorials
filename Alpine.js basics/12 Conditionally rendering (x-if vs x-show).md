x-if example
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
		<!-- Example with x-show -->
		<div x-data="{ show: false }">
			<div>
				<span x-show="show">Am I invisible?</span>
			</div>
			<button x-on:click="show=!show">Show</button>
		</div>

		<!-- 
			Example with x-if 
			- we need to use template with x-if
			- x-if should be used if there is more 'intensive' work to be done
		-->
		<div x-data="{ show: false }">
			<div>
				<template x-if="show">
					<span x-show="show">Am I invisible?</span>
				</template>
			</div>
			<button x-on:click="show=!show">Show</button>
		</div>

	</body>
</html>
```

x-if more 'intensive'
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
		<!-- Example -->
		<div
			x-data="{ 
			show: false,
			users: [
				{id: 1, name:'Alex', points: 10},
				{id: 2, name:'Billy', points: 20},
				{id: 3, name:'Mabel', points: 30}
			],
			
			usersOrderedByPoints () {
				console.log('sort')
				return this.users.sort( (a,b) => b.points - a.points)
			}
		}"
		>
			<button x-on:click="show=!show">Show</button>

			<template x-if="show">
				<template x-for="user in usersOrderedByPoints()">
					<div>
						<span x-text="user.name"></span> <span x-text="user.points"></span>
					</div>
				</template>
			</templa>
		</div>
	</body>
</html>
```