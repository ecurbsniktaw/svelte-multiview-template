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

View number 3

<br><br>

<a
href
on:click|preventDefault={()=>mouseClicked('setValue', '5968')}>
Set parameter==5968
</a>
