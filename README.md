# svelte-multiview-template
This template illustrates use of custom events as a method for switching between views in a Svelte application. 

## App.svelte

The App component outputs the navigation bar, and then decides which view to output based on the value of the "whichView" variable.

```{#if whichView=='one'}
<Navbar on:mouseclicked={handleClick} />
{#if domView=='one'}
  <View1 on:mouseclicked={handleClick} />
{:else if domView=='two'}
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
```

## Links in Views and in the Nav Component

Each component that displays a view (and also the Navbar component) needs to include this code:

```
import { createEventDispatcher } from "svelte";
const dispatch = createEventDispatcher();

function mouseClicked(what, value, name) {
  let eventObj = {
    what: what,
    value: value,
    name: name
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

As an illustration of updating the DOM automatically when one or more values change, App.svelte includes this code:

```
The number is {domValue['one']}<br>
The author is {domValue['two']}<br>
```

Clicking a link like the following will update the display to show the new parameter value:

```
<a
href
on:click|preventDefault={()=>mouseClicked('setValue', '42', 'one')}>
Set the number to 42
</a>
```

## To Do

- Add code that changes a watched value by entering it into a form field.
- Find a way to avoid writing the mouseClicked code in every component.