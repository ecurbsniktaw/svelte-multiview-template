# svelte-multiview-template
This template illustrates use of custom events as a method for switching between views in a Svelte application. The App component outputs the navigation bar, and then decides which view to output based on the value of the "whichView" variable.

```{#if whichView=='one'}
<Navbar on:mouseclicked={handleClick} />
{#if whichView=='one'}
  <View1 on:mouseclicked={handleClick} />
{:else if whichView=='two'}
  <View2 on:mouseclicked={handleClick} />`
{:else}
  <View3 on:mouseclicked={handleClick} />
{/if}
```

Notice that each component is expected to generate custom "mouseclicked" events. The handleClick function, in App, handles those events:

```
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
```

