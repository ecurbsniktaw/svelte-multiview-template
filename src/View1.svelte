<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    function mouseClicked(what, value) {
        let eventObj = {
            what: what,
            value: value
        }
        dispatch("mouseclicked", eventObj);
    }
</script>

<h3>This is view number one</h3>

<a
href
on:click|preventDefault={()=>mouseClicked('switchView', 'two')}>
Click to go to view two
</a>

<br><br>

<a
href
on:click|preventDefault={()=>mouseClicked('setValue', '42')}>
Set parameter==42
</a>

