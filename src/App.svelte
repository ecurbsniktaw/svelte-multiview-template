<script>
	import Navbar from "./Navbar.svelte";
	import View1  from "./View1.svelte";
	import View2  from "./View2.svelte";
	import View3  from "./View3.svelte";
  
	// At startup, show the first view and initialize the parameter.
	let whichView = 'one';
	let theParam  = "123";

	function handleClick(event) {
		let whatHappened = event.detail.what;
		let whatValue    = event.detail.value;
		if (whatHappened=='switchView') {
			whichView = whatValue;
		}
		else if (whatHappened=='setValue') {
			theParam = whatValue;
		}
	}
  </script>
  
  <Navbar on:mouseclicked={handleClick} />

  The Parameter Value is {theParam}<br><br>

  {#if whichView=='one'}
	<View1 on:mouseclicked={handleClick} />

  {:else if whichView=='two'}
	<View2 on:mouseclicked={handleClick} />
	  
  {:else}
	<View3 on:mouseclicked={handleClick} />

  {/if}
