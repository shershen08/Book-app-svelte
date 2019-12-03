<script>
  import { Router, Link, Route } from "svelte-routing";
  import Books from "./pages/Books.svelte";
  import About from "./pages/About.svelte";
  import User from "./pages/User.svelte";

  export let url = "";
	
</script>

<Router url="{url}">
  <nav>
    <Link to="/">Books</Link>
    <Link to="about">About</Link>
    <Link to="user">Blog</Link>
    <h1>dfghjkl</h1>
  </nav>
  <div>
    <Route path="about" component="{About}" />
    <Route path="user" component="{User}" />
    <Route path="/"><Books /></Route>
  </div>
</Router>

<style lang="scss">
$white: #fff;
$darkGray: #333;
// @import './common.sccss';

nav {
  background: blue;
  
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