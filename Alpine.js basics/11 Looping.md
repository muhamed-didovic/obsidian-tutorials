
simple loop
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
		- 'template' tag is needed for loops
		-->
		<div x-data="{ numbers: [1,2,3,4,5] }">
			<template x-for="number in numbers">
				<span x-text="number"></span>
			</template>
		</div> 
	</body>
</html>
```

ordered ist
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

		<!-- simple exmaple -->
		<!-- <div x-data="{ fruits: ['apple','banana','orange','grapes'] }">
			<template x-for="fruit, index in fruits">
				<div><span x-text="index+1"></span> <span x-text="fruit"></span></div>
			</template>
		</div> -->

		<!--simple order list -->
		<div x-data="{ fruits: ['apple','banana','orange','grapes'] }">
			<ol>
				<template x-for="fruit in fruits">
					<li x-text="fruit"></li>
				</template>
			</ol>	
	
		</div>

		<!-- list with 'index' from for in loop -->
		<div x-data="{ fruits: ['apple','banana','orange','grapes'] }">
			<template x-for="fruit, index in fruits">
				<li><span x-text="index+1"></span> <span x-text="fruit"></span></li>
			</template>
			
		</div>
	</body>
</html>
```

array of objects with 'key'
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
		- using 'key' in loops gives Alipine a unique reference for each iteration or people in loop, so DOM updates then it knows where the person is or how to organize it
		 -->
		<div
			x-data="{ 
				people:[	
					{id: 1, name: 'Alex'},
					{id: 2, name: 'Billy'},
					{id: 3, name: 'Mabel'}
				]
		}"
		>
			<template x-for="person in people" :key="person.id">
				<div x-text="person.name"></div>
			</template>
		</div> 

	
	</body>
</html>
```

more complex example to demonstrate the importance of having 'key' in loops
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
		 - basically when there is a change in DOM, Alpine can't track any more in the right way the changes and apply them
		 -->
		<div
			x-data="{ 
				people:[	
					{id: 1, points: 1, name: 'Alex'},
					{id: 2, points: 8, name: 'Billy'},
					{id: 3, points: 5, name: 'Mabel'}
				],
				incrementPoints (id) {
					this.people.find((p) => p.id === id).points++
				},
				get peopleSortedByPoints () {
					return this.people.sort( (a,b) => a.points - b.points)
				}
		}"
		>
			<template x-for="person in peopleSortedByPoints" :key="person.id">
				<div>
					<span x-text="person.name"></span> (<span
						x-text="person.points"
					></span
					>)
					<button x-on:click="incrementPoints(person.id)">Increment</button>
				</div>
			</template>
		</div>
	</body>
</html>
```