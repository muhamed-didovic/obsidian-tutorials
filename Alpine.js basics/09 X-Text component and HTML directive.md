x-text with any element:
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
		<!-- we can use an expression in x-text component, thi is used for simple text and we can't insert any html -->
		<div x-data="{ hello: 'world' }">
			<h1 x-text="hello.toUppeCase()"></h1>
		</div>
	</body>
</html>
```

html directive:
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
		<div x-data="{ body: ' <strong>Hello world</strong>' }">
			<div x-html="body"></div>
		</div>
	</body>
</html>
```