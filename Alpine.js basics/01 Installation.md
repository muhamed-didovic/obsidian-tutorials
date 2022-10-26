here is the link to the site: https://alpinejs.dev/ and how to start or install: https://alpinejs.dev/start-here 

```html
<html>

<head>

<script defer src="https://unpkg.com/alpinejs@3.x.x/dist/cdn.min.js"></script>

</head>

<body>

	<h1 x-data="{ message: 'I ❤️ Alpine' }" x-text="message"></h1>

</body>

</html>
```

Starter template as well:

```html
<script src="//unpkg.com/alpinejs" defer></script>

<div x-data="{ open: false }">
	<button @click="open = true">Expand</button>
	<span x-show="open">
	Content...
	</span>
</div>
```