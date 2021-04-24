<script>
	import Navbar from "./Navbar.svelte";
	import View1  from "./View1.svelte";
	import View2  from "./View2.svelte";
	import View3  from "./View3.svelte";
  
	// At startup, show the first view and initialize the parameter values.
	let domView;
	let domValue = [];

	function resetDisplay () {
		domView             = 'one';
		domValue['number']  = "123";
		domValue['author']  = "Shakespeare";
	}

	function handleClick(event) {
		let whatHappened = event.detail.what;
		let whatValue    = event.detail.value;

		if (whatHappened=='switchView') {
			domView = whatValue;
		}

		else if (whatHappened=='setValue') {
			let whatName = event.detail.name;
			domValue[whatName] = whatValue;
		}

		else if (whatHappened=='reset') {
			resetDisplay();
		}

		else {
			alert('In function handleClick in App.svelte: incorrect whatHappened value [' + 
			whatHappened + 
			'] when handling a custom mouseclicked event.')
		}
	}

	resetDisplay();

  </script>
  
  <Navbar on:mouseclicked={handleClick} />

  The number is {domValue['number']}<br>
  The author is {domValue['author']}<br>

  {#if domView=='one'}
	<View1 on:mouseclicked={handleClick} />

  {:else if domView=='two'}
	<View2 on:mouseclicked={handleClick} />
	  
  {:else}
	<View3 on:mouseclicked={handleClick} />

  {/if}
