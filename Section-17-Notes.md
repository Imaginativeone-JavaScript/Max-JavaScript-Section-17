- [ ] 17 01:17:16 | Async JavaScript: Promises & Callbacks  
	- [x] 348 01 Module Introduction | 01:12
	  - Code that "Takes a Bit Longer"
		- What is "Async Code"?
		- Callbacks
		- Promises
		- async/await
	- [x] 349 02 Understanding Synchronous Code Execution ("Sync Code") | 02:51
	  - JavaScript is Single-Threaded
		- JS Can only execute one task at a time.
	- [x] 350 03 Understanding Asynchronous Code Execution ("Async Code") | 05:44
	  - Using only one thread can have a downside
		- Certain operations can take a bit longer
		- [console.log()][---- setTimeout() ----][-- moreCode() --]
		  - HTTP Requests/Responses
			- Location Requests/Responses
			- Database Requests/Responses
		- Asynchronous Code Execution
			- Time-heavy operations are handed off to the Browser, which CAN use multiple threads
			- The Browser needs a way to communicate back with our JavaScript Code
				- Callback functions
				- The Browser steps back into our script and executes something there, once its operation is done.
				With:
				```javascript
				const button = document.querySelector('button');
				const output = document.querySelector('p');

				function trackUserHandler() {
					console.log('Clicked!);
				}

				button.addEventListener('click', trackUserHandler);
				```
				  - We hand off this task to the Browser, which manages this task behind the scenes.
					- The Browser steps back into the handler function, once a click occurs.
	
	- [ ] 351 04 Blocking Code & The "Event Loop" | 10:30

		```javascript
		const button = document.querySelector('button');
		const output = document.querySelector('p');

		function trackUserHandler() {
		  console.log('Clicked!);
		}

		button.addEventListener('click', trackUserHandler);

		let result = 0; // This is NOT handed off to the Browser
		for (let i = 0; i < 100000000; i++) {
			result =+ i;
		}
		```

		All the click events happen AFTER the loop is complete.

		  #### The Event Loop
			https://developer.mozilla.org/en-US/docs/Mozilla/Gecko/Chrome/API/Browser_API/Using

	- [ ] 352 05 Sync + Async Code - The Execution Order | 04:03

		Callbacks	
		```javascript
		const button = document.querySelector('button');
		const output = document.querySelector('p');

		function trackUserHandler() {
			navigator.geolocation.getCurrentPosition(
				positionData => {
					console.log(positionData);
				},
				error => {
					console.log(error);
				}
			);
		}

		button.addEventListener('click', trackUserHandler);
		```

	- [ ] 353 06 Multiple Callbacks & setTimeout(0) | 03:20

		Nested Callbacks
		```javascript
		const button = document.querySelector('button');
		const output = document.querySelector('p');

		function trackUserHandler() {
			navigator.geolocation.getCurrentPosition(
				positionData => {
					setTimeout(() => {
						console.log(positionData);
					}, 2000);
				},
				error => {
					console.log(error);
				}
			);
			setTimeout(() => {
				console.log(positionData);
			}, 0);
			console.log('Getting position...'); // This executes first, because it's in the stack first
		}

		button.addEventListener('click', trackUserHandler);
		```

	- [ ] 354 07 Getting Started with Promises | 08:25
	  - Nested callbacks can be difficult to read

		```javascript
		const button = document.querySelector('button');
		const output = document.querySelector('p');

		const setTimer = (duration) => {

			const promise = new Promise((resolve, reject) => {

				setTimeout(() => {

					resolve('Done!'); // Any value can be passed.

				}, duration);

			}); // The Promise constructor function is called right away.

			return promise;

		}

		function trackUserHandler() {
			navigator.geolocation.getCurrentPosition(
				positionData => {
					setTimer(2000).then(data => {
						console.log(data, positionData);
					});
				},
				error => {
					console.log(error);
				}
			);
			setTimer(1000).then(() => {
				console.log('Timer done!');
			});

			console.log('Getting position...'); // This executes first, because it's in the stack first
		}

		button.addEventListener('click', trackUserHandler);
		```

	- [ ] 355 08 Chaining Multiple Promises | 05:53
	  - The Promise-success(ful) results are returned step by step.
	- [ ] 356 09 Promise Error Handling | 07:46  
	  - Errors are not handled with the normal .then()
		- catch() is an alternative to errors and error handling
		  - does not cancel the Promise, but allows it to continue
	- [ ] 357 10 Promise States & "finally" | 00:41  
	- [ ] 358 11 Async/ await | 09:11
	  - Only in functions
		- Returns a Promise
		- await in front of each internal Promise
		- Does NOT block execution
		- Just transforms the code behind the scenes
	- [ ] 359 12 Async/ await & Error Handling | 03:07
	  - try/catch can be used here  
	- [ ] 360 13 Async/ await vs "Raw Promises" | 04:56
	- [ ] 361 14 Promise.all(), Promise.race() etc. | 07:59
	  - Multiple Promises that I want to orchestrate
		- Promise.race() // static method to get the faster of two Promises
		- Promise.all()  // The data is the COMBINATION of all the (Promise) data (as an array).
	- [ ] 362 15 Wrap Up | 01:27
	- [ ] 363 16 Useful Resources & Links | 00:10