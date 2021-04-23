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
Click to go to view two
</a>

<br><br>

<a
href
on:click|preventDefault={()=>mouseClicked('setValue', '42', 'one')}>
Set the number to 42
</a>

<br><br>

<a
href
on:click|preventDefault={()=>mouseClicked('setValue', 'Homer', 'two')}>
Set the author to Homer
</a>

<br><br>

<a
href
on:click|preventDefault={()=>mouseClicked('reset')}>
Reset the parameters
</a>

<br><br>

<a
href
on:click|preventDefault={()=>mouseClicked('nothing')}>
Generate an error
</a>

