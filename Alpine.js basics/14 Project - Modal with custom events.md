
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
		body {
			margin: 0;
		}

		.modal-wrapper {
			position: absolute;
			width: 100%;
			height: 100%;
			background-color: rgba(0, 0, 0, 0.5);
			display: flex;
			align-items: center;
			justify-content: center;
		}

		.modal {
			width: 100%;
			max-width: 30%;
			background-color: #ffff;
			padding: 20px;
		}
	</style>

	<body>
		<!--
		- here is used  'window' modifier, so we are aware that escape button is pressed globally(or listening globally) not on div
		 -->
		<div
			class="modal-wrapper"
			x-data="{ open:false }"
			x-show="open"
			x-on:open-modal.window="open = true"
			x-on:keyup.escape.window="open=false"
		>
			<div class="modal" x-on:click.outside="open = false">I'm a Modal</div>
		</div>
		<button x-data x-on:click="$dispatch('open-modal')">Trigger Modal</button>

		
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

	<style>
		body {
			margin: 0;
		}

		.modal-wrapper {
			position: absolute;
			width: 100%;
			height: 100%;
			background-color: rgba(0, 0, 0, 0.5);
			display: flex;
			align-items: center;
			justify-content: center;
		}

		.modal {
			width: 100%;
			max-width: 30%;
			background-color: #ffff;
			padding: 20px;
		}
	</style>

	<body>
		
		<!-- sending data from a event -->
		<div
			x-data="{ message: '' }"
			x-on:message.window="message = $event.detail.message"
		>
			<span x-text="message"></span>
		</div>
		<button x-data x-on:click="$dispatch('message', { message:'Hello There' })">
			Set Message
		</button>
	</body>
</html>
```