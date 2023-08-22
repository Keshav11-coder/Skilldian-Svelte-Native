<script>
    export let scale = 0.9;
    export let color = "white";
</script>

<stackLayout orientation="horizontal" width="26" height="100%"  scaleX={scale} scaleY={scale}>
    <stackLayout backgroundColor={color} width="6" height="6" borderRadius="50%" marginRight="2"></stackLayout>
    <stackLayout backgroundColor={color} width="6" height="6" borderRadius="50%" marginRight="2"></stackLayout>
    <stackLayout backgroundColor={color} width="6" height="6" borderRadius="50%" ></stackLayout>
</stackLayout>