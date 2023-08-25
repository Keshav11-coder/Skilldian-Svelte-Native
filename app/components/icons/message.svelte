<script>
    export let color = "white";
    export let scale=0.9;
</script>

<stackLayout orientation="vertical" width="24" scaleX={scale} scaleY={scale} marginTop="3">
    <stackLayout width="23" height="16" backgroundColor={color} borderRadius="6px"></stackLayout>
    <stackLayout marginRight="-5" marginTop="-0.5" width="8" backgroundColor="transparent" borderWidth="8px" borderTopColor={color} borderBottomColor="transparent"borderLeftColor="transparent"borderRightColor="transparent"></stackLayout>
</stackLayout>