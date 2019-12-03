<script>
  import { Router, Link, Route } from "svelte-routing";
  import Books from "./pages/Books.svelte";
  import About from "./pages/About.svelte";
  import User from "./pages/User.svelte";
  import Grid from "./pages/Grid.svelte";

  export let url = "";
	
</script>

<Router url="{url}">
  <nav>
    <Link to="/">Books</Link>
    <Link to="about">About</Link>
    <Link to="user">Blog</Link>
    <Link to="grid">Grid</Link>
  </nav>
  <div>
    <Route path="about" component="{About}" />
    <Route path="user" component="{User}" />
    <Route path="grid" component="{Grid}" />
    <Route path="/"><Books /></Route>
  </div>
</Router>

<style lang="scss">
$white: #fff;
$darkGray: #333;
// @import './common.sccss';

nav {
  background: #f1f1f1;
  
  a {
    color: $white;
  }

  h1 {
      color:$white;

  }
}

  h1 {
      color:$darkGray;
      
  }


section{
    margin: auto;
    width :30rem;
    
}

label,input,textarea{width: 100%}
</style>