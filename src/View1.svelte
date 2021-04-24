<script>
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
</script>

<h3>View Number One</h3>

<a
href
on:click|preventDefault={()=>mouseClicked('switchView', 'two')}>
Go to view two
</a>

|

<a
href
on:click|preventDefault={()=>mouseClicked('setValue', '42', 'number')}>
Set the number to 42
</a>

|

<a
href
on:click|preventDefault={()=>mouseClicked('setValue', 'Homer', 'author')}>
Set the author to Homer
</a>

|

<a
href
on:click|preventDefault={()=>mouseClicked('reset')}>
Reset the values
</a>

|

<a
href
on:click|preventDefault={()=>mouseClicked('nothing')}>
Generate an error
</a>

