<script>

// App.svelte
//	This is part of a template for multi-view Svelte apps.

	import Navbar from "./Navbar.svelte";
	import View1  from "./View1.svelte";
	import View2  from "./View2.svelte";
	import View3  from "./View3.svelte";
  
	let whichView = 'one'; // At startup, show the first view.

	function navClicked(event) {
		whichView = event.detail;
	}
  
  </script>
  
  <style>
  </style>
  
  <Navbar
	on:oneclicked={navClicked}
	on:twoclicked={navClicked}
	on:threeclicked={navClicked}
  />

  {#if whichView=='one'}
	<View1 />

  {:else if whichView=='two'}
	<View2 />
	  
  {:else}
  	<View3 />

  {/if}
