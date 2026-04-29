<script setup>
if ("geolocation" in navigator) {
    navigator.geolocation.getCurrentPosition((position) => {
        console.log(position.coords.latitude, position.coords.longitude)
    })
} else {
    /* geolocation IS NOT available */
}
</script>

<template>

</template>