<script>
  export let scale = 0.9;
  export let color = "white";
</script>

<stackLayout
  width="100%"
  height="28"
  orientation="vertical"
  marginTop="6"
  scaleX={scale}
  scaleY={scale}
>
  <stackLayout
    class="top"
    backgroundColor="white"
    width="16"
    height="6"
    borderTopLeftRadius="6px"
    borderTopRightRadius="6px"
  />
  <absolutelayout width="16">
    <stackLayout
      class="box"
      borderWidth="8"
      borderRightColor="white"
      borderLeftColor="white"
      borderTopColor="white"
      borderBottomColor="transparent"
    />
    <stackLayout width="16" height="8" backgroundColor="white" marginTop="0" />
  </absolutelayout>
</stackLayout>
