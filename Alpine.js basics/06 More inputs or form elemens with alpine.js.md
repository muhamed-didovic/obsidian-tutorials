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
	<!-- Checkbox -->
	<div x-data="{ agreed: false }">
		<input type="checkbox" x-model="agreed" />
		<span x-show="agreed"> You have agreed! </span>
	</div>  

	<!-- Checkboxes -->
	<div x-data="{ records: [] }">
	
		<input type="checkbox" x-model="records" value="1">
		<input type="checkbox" x-model="records" value="2">
		<input type="checkbox" x-model="records" value="3">
		<span x-text="records"></span>

	</div>
	
	<form

		x-data="{
		
			users: [],
			
			deleteUsers () {
			
			console.log(this.users)
			
			}
		
		}"
		
		x-on:submit.prevent="deleteUsers"
	>		
		
		<input type="checkbox" x-model="users" value="1" />
		Pepito
		
		<input type="checkbox" x-model="users" value="2" />
		Sutanito
		
		<input type="checkbox" x-model="users" value="3" />
		Perencejito
		
		<button type="submit">Delete</button>
		
	</form>
	
	<!-- Dropdown -->
	<div x-data="{ plan: '' }">
	
		<select x-model="plan">
		<option value="">Select an Option</option>
		<option value="yearly">Yearly</option>
		<option value="monthly">Monthly</option>
		<option value="daily">Daily</option>
		</select>
	
		<span x-show="plan" x-text="`You've chosen the ${plan} plan.`"></span>
	
	</div>
	
	<!-- Radio -->
	<div x-data="{ plan: 'monthly' }">
	
		<input type="radio" name="plan" value="monthly" x-model="plan" />
		
		<input type="radio" name="plan" value="yearly" x-model="plan" />
		
		<span x-show="plan" x-text="`You've chosen the ${plan} plan.`"></span>
	
	</div>
  
</body>  
</html>
```
