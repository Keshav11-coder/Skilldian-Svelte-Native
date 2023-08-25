<script lang="ts">
  /*import Home0 from "./parts/Homev0.svelte";*/
  import Home from "./components/Home.svelte";
  import HomeNavBugfx from "./components/Home_nav_bugfx.svelte";
  import Account from "./components/Account.svelte"
  import Search from "./components/Search.svelte"
  import Nav from "./components/Nav.svelte"
  let page = 0;
</script>

<frame>
  <!--<Home0 />-->
  {#if page === 0}
  <Home bind:page />
  {:else if page === 1}
  <Account bind:page/>
  {:else if page === 2}
  <Search bind:page/>
  {/if}
  <!--<HomeNavBugfx />-->
</frame>
