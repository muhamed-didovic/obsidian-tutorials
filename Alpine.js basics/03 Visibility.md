To show or hide element x-show component is used:
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
	<div x-data="{visible: false}">  
		<div x-show="visible">Some content</div>
	</div>  
  
</body>  
</html>
```

Using arrays:

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
	<div x-data="{records: [1,2,3,4]}">  
		<span x-show="records.length > 0">Show Records</span>  
	</div>  
  
</body>  
</html>
```

Click event to show:

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
	<div x-data="{show: false}"> 
	<button x-on:click="show = true">Show</button> 
		<span x-show="show"></span>  
	</div>  
  
</body>  
</html>
```

Toggle:

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
	<div x-data="{show: false}"> 
	<buton x-on:click="show = !show">Toggle</button> 
		<span x-show="show"></span>  
	</div>  
  
</body>  
</html>
```

Number incrementer:

```html
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
	<div x-data="{number: 0}">  
    <button x-on:click="number++">Icrement</button>  
        <span x-text="number"></span>  
        <div x-show="number >= 10">Big number</div>  
	</div>
  
</body>  
</html>
```

