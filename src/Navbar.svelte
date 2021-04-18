<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    function oneClicked() {
      dispatch("oneclicked", 'one');
    }
    function twoClicked() {
      dispatch("twoclicked", 'two');
    }
    function threeClicked() {
      dispatch("threeclicked", 'three');
    }
</script>

<style>

    ul.topnav {
      list-style-type: none;
      margin: 0;
      margin-bottom: 0.5rem;
      padding: 0;
      overflow: hidden;
      background-color: #999999;
    }
  
    ul.topnav li {
      float: left;
    }
  
    ul.topnav li a {
      display: block;
      color: white;
      text-align: center;
      padding: 0.5rem 0.5rem;
      text-decoration: none;
    }
  
    ul.topnav li a:hover:not(.active) {
      background-color: #111;
    }
  
    @media screen and (max-width: 600px) {
      ul.topnav li {
        float: none;
      }
    }

</style>

<ul class="topnav">

    <li>
      <a
        href
        on:click|preventDefault={oneClicked}>
        ViewOne
      </a>
    </li>

    <li>
        <a
          href
          on:click|preventDefault={twoClicked}>
          ViewTwo
        </a>
    </li>
  
    <li>
        <a
          href
          on:click|preventDefault={threeClicked}>
          ViewThree
        </a>
    </li>
  
</ul>
