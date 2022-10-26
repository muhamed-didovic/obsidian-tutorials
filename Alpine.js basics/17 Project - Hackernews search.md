
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
		<div
			x-data="{
				query: '',
				results: [],
		
				performSearch (query) {
				//Hacker news
					fetch(`https://hn.algolia.com/api/v1/search?query=${query}`)
						.then(response => response.json())
						.then(results => this.results = results.hits)
				},
				init () {
					this.$watch('query', (query) => {
						if (query === '') {
							this.results = []
							return
						}
						this.performSearch(query)
					})
				}
			}"
		>
			<input type="text" x-model.debounce.750="query" />
			<p x-show="query.length">
				Your search for <span x-text="query"></span> returned
				<span x-text="results.length"></span> results
			</p>

			<div>
				<template x-for="result in results" :key="result.objectID">
					<div>
						<h4 x-text="result.title"></h4>
						<a x-bind:href="result.url" x-text="result.url"></a>
					</div>
				</template>
			</div>
		</div>
	</body>
</html>
Footer

```