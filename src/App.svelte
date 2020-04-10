<script>
  // pages
  import Home from "./Home.svelte";
  import Projects from "./Projects.svelte";
  import Blog from "./Blog.svelte";
  import Timeline from "./Timeline.svelte";
  import Resume from "./Resume.svelte";
  import Contact from "./Contact.svelte";
  export let menu = 1;
</script>

<style>
  :global(body) {
    background-color: #1fc8db;
    background-image: linear-gradient(
      141deg,
      #9fb8ad 0%,
      #1fc8db 51%,
      #2cb5e8 75%
    );
    font-family: "Amatic SC", cursive;
    font-size: 1.25em;
  }
  ul#menu li {
    display: inline;
    padding: 0 auto;
  }
  #main {
    margin-block-start: 3.3em;
    display: grid;
    grid-template-columns: 1fr 3fr 1fr;
    width: 100%;
    height: 92vh;
    position: fixed;
  }
  #nav {
    position: fixed;
    top: 0;
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
  }

  #menu {
    justify-self: center;
    padding: 0;
    border-bottom: 1px solid aliceblue;
    padding-block-end: 1em;
    margin-block-end: 0;
    color: aliceblue;
  }
  a {
    color: aliceblue;
    text-decoration: none;
  }
</style>

<div id="main">
  {#if menu === 1}
    <Home />
  {:else if menu === 2}
    <Projects />
  {:else if menu === 3}
    <Blog />
  {:else if menu === 4}
    <Timeline />
  {:else if menu === 5}
    <Resume />
  {:else if menu === 6}
    <Contact />
  {:else}
    <h1>We lost you.</h1>
  {/if}

</div>
<nav id="nav">
  <ul id="menu">
    <li>
      <a href="/home" on:click|preventDefault={() => (menu = 1)}>c-vega</a>
    </li>
    |
    <li>
      <a href="/projects" on:click|preventDefault={() => (menu = 2)}>
        projects
      </a>
    </li>
    |
    <li>
      <a href="/blog" on:click|preventDefault={() => (menu = 3)}>blog</a>
    </li>
    |
    <li>
      <a href="/timeline" on:click|preventDefault={() => (menu = 4)}>
        timeline
      </a>
    </li>
    |
    <li>
      <a href="/resume" on:click|preventDefault={() => (menu = 5)}>resume</a>
    </li>
    |
    <li>
      <a href="/contact" on:click|preventDefault={() => (menu = 6)}>contact</a>
    </li>
  </ul>
</nav>
