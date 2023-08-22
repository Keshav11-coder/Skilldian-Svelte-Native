<!--
    this file imports all the available icons and acts like a master branch.
    it mostly consists of if-statements and argument handlers to help clean
    up the main frame.

    the code does NOT add any other parents around the icons except for a
    stackLayout, which helps the icon we used in the main frame.
-->

<script>
  export let iconColor;
  export let iconSize;
  export let iconIndex;
  export let IconActivated = false;

  // import all the available icons

  import Heart from "./heart.svelte";
  import Message from "./message.svelte";
  import Share from "./share.svelte";
  import Bookmark from "./bookmark.svelte";
  import More from "./more.svelte";
</script>

{#if iconIndex === 0}
  <stackLayout width="100%" height="100%" verticalAlignment="center"
    ><Heart color={iconColor} scale={iconSize} activated={false} /></stackLayout
  >
{:else if iconIndex === 1}
  <stackLayout width="100%" height="100%" verticalAlignment="center"
    ><Share color={iconColor} scale={iconSize} /></stackLayout
  >
{:else if iconIndex === 2}
  <stackLayout width="100%" height="100%" verticalAlignment="center"
    ><Bookmark color={iconColor} scale={iconSize} /></stackLayout
  >
{:else if iconIndex === 3}
  <stackLayout width="100%" height="100%" verticalAlignment="center"
    ><More color={iconColor} scale={iconSize} /></stackLayout
  >
{:else if iconIndex === 4}
  <stackLayout width="100%" height="100%" verticalAlignment="center"
    ><Message color={iconColor} scale={iconSize} /></stackLayout
  >
{/if}
