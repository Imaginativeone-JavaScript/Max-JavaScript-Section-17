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
	- [ ] 352 05 Sync + Async Code - The Execution Order | 04:03  
	- [ ] 353 06 Multiple Callbacks & setTimeout(0) | 03:20  
	- [ ] *** ** Asynchronous Code 3 questions  
	- [ ] 354 07 Getting Started with Promises | 08:25  
	- [ ] 355 08 Chaining Multiple Promises | 05:53  
	- [ ] 356 09 Promise Error Handling | 07:46  
	- [ ] 357 10 Promise States & "finally" | 00:41  
	- [ ] 358 11 Async/ await | 09:11  
	- [ ] 359 12 Async/ await & Error Handling | 03:07  
	- [ ] 360 13 Async/ await vs "Raw Promises" | 04:56  
	- [ ] 361 14 Promise.all(), Promise.race() etc. | 07:59  
	- [ ] *** ** Promises & async/ await 5 questions
	- [ ] 362 15 Wrap Up | 01:27
	- [ ] 363 16 Useful Resources & Links | 00:10