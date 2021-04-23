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

<h3>View Number Three</h3>

<a
href
on:click|preventDefault={()=>mouseClicked('setValue', '5968', 'one')}>
Set the number to 5968
</a>
