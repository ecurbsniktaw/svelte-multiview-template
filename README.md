# svelte-multiview-template
This template illustrates use of custom events as a method for switching between views in a Svelte application. 

## App.svelte

The App component outputs the navigation bar, and then decides which view to output based on the value of the "whichView" variable.

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

## Links in Views and in the Nav Component

Each component that displays a view (and also the Navbar component) needs to include this code:

```
import { createEventDispatcher } from "svelte";
const dispatch = createEventDispatcher();
function mouseClicked(what, value) {
  let eventObj = {
    what: what,
    value: value
  }
  dispatch("mouseclicked", eventObj);
}
```
Links that raise a mouseclicked event in order to change the view that is being displayed look like this:

```
<a
href
on:click|preventDefault={()=>mouseClicked('switchView', 'two')}>
Click to go to view two
</a>
```

## Links that change a value that updates the DOM

As an illustration of updating the DOM automatically when a value changes, App.svelte includes this code:

```
The Parameter Value is {theParam}
```

Clicking a link like the following will update the display to show the new parameter value:

```
<a
href
on:click|preventDefault={()=>mouseClicked('setValue', '42')}>
Set parameter==42
</a>
```

## To Do

- Generalize the setValue option in the handleClicked function so that any variable can be set.
- Check for invalid value of event.detail.what in handleClick.
- Add code that changes a watched value by entering it into a form field.
- Find a way to avoid writing the mouseClicked code in every component.