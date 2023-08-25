<script>
  export let activated = false;
  export let color = "white";
  export let scale = 0.85;
</script>

<absoluteLayout
  class="group"
  width="26"
  height="100%"
  scaleX={scale}
  scaleY={scale}
  marginTop="9"
>
<stackLayout orientation="vertical" width="26" height="30">
    <stackLayout width="18" height="3" backgroundColor={color} marginTop="11"/>
    <stackLayout width="18" height="3" backgroundColor={color} marginTop="-3" rotate="90deg"  />
</stackLayout>
</absoluteLayout>

<style></style>
