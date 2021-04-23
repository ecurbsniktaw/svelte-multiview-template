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

<ul class="topnav">

    <li>
        <a
          href
          on:click|preventDefault={()=>mouseClicked('switchView', 'one')}>
          ViewOne
        </a>
    </li>`
  
    <li>
        <a
          href
          on:click|preventDefault={()=>mouseClicked('switchView', 'two')}>
          ViewTwo
        </a>
    </li>
  
    <li>
        <a
          href
          on:click|preventDefault={()=>mouseClicked('switchView', 'three')}>
          ViewThree
        </a>
    </li>

</ul>

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
