<script context="module">
    // import { createEventDispatcher } from "svelte";
    // const dispatch = createEventDispatcher();

    export function mouseClicked(what, value) {
        let eventObj = {
            what: what,
            value: value
        }
        dispatch("mouseclicked", eventObj);
    }
</script>