<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    function clickedToTwo() {
      dispatch("twoclicked", 'two');
    }

    function handleClick(param) {
        dispatch("paramClicked", param);
    }

</script>

View number 3
<br><br>
<a
href
on:click|preventDefault={() => handleClick("5968")}>
Set parameter==5968
</a>
