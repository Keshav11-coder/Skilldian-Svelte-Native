<script>
  export let activated = false;
  export let color = "white";
  export let scale = 0.85;
</script>

<absoluteLayout
  class="group"
  orientation="vertical"
  width="23"
  height="30"
  scaleX={scale}
  scaleY={scale}
>
  <stackLayout orientation="horizontal" width="18" height="10" marginTop="14">
    <stackLayout
      width="6.25"
      height="10"
      backgroundColor={color}
      borderBottomLeftRadius="6px"
    />
    <stackLayout width="6" height="10" />
    <stackLayout
      width="6.25"
      height="10"
      backgroundColor={color}
      borderBottomRightRadius="6px"
    />
  </stackLayout>
  <stackLayout width="18" height="8" backgroundColor={color} marginTop="10" borderRadius="2" />
  <stackLayout borderWidth="9" borderBottomColor={color} borderTopColor="transparent" borderLeftColor="transparent" borderRightColor="transparent" marginTop="-7">

  </stackLayout>
</absoluteLayout>

<style></style>
