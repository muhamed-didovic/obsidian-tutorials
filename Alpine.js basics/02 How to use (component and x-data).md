Alpine components and a starter template

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
	<div x-data="{hello: 'world'}">  
		<span x-text="hello + ' something else'"></span>  
	</div>  
  
</body>  
</html>
```

so to show value for x-data component, we use x-text component to grab and show the output of the variable, we can also use expression inside x-text component: `x-text="2+2"`