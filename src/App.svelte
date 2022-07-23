<script>
  import { Router, Route, Link } from "svelte-navigator";
  import Landing from "./landing/Landing.svelte";
  import Comprar from "./comprar/Comprar.svelte";
  import Trying from "./comprar/Trying.svelte";
  import Thanks from "./comprar/Thanks.svelte";
</script>


<main>

  <Router>
    <Route primary={false} path="/"><Landing/></Route>
    <Route primary={false} path="comprar"><Comprar/></Route>
    <Route primary={false} path="comprar/processing"><Trying/></Route>
    <Route primary={false} path="comprar/thanks"><Thanks/></Route>
      
  </Router>
  
</main>


<style>

  main{
    width: 100vw;
    height: 100vh;
  }
  
</style>