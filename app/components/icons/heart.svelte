<script>
  export let activated = false;
  export let color = "white";
  export let scale = 0.9;
</script>

{#if !activated}
  <stackLayout
    class="group"
    orientation="vertical"
    width="100%"
    height="100%"
    marginTop="6"
    scaleX={scale}
    scaleY={scale}
  >
    <stackLayout
      orientation="horizontal"
      width="22.5"
      height="65%"
      marginRight="-1"
    >
      <stackLayout
        class="1"
        marginRight="-1"
        backgroundColor={color}
        width="11.5"
        height="14"
        borderRadius="60%"
      />
      <stackLayout
        class="2"
        marginLeft="-1"
        backgroundColor={color}
        width="11.5"
        height="14"
        borderRadius="60%"
      />
    </stackLayout>
    <stackLayout
      width="21.5"
      height="12"
      marginTop="-12"
      backgroundColor={color}
      borderBottomLeftRadius="100%"
      borderBottomRightRadius="100%"
    />
  </stackLayout>
{/if}

<style></style>
