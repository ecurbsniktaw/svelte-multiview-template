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

<h3>This is view number one. </h3>

<a
href
on:click|preventDefault={clickedToTwo}>
Click to go to view two
</a>
<br><br>
<a
href
on:click|preventDefault={() => handleClick("42")}>
Set parameter==42
</a>
