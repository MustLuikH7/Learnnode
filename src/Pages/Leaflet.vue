<script setup>
import { ref } from 'vue';
import LeafletMap from '../Components/LeafletMap.vue';
let center = ref([59.42699949642546, 24.743485211156457])
let coords = ref([0, 0]);

if ("geolocation" in navigator) {
    setInterval(() => {
        navigator.geolocation.getCurrentPosition((position) => {
            console.log(position.coords.latitude, position.coords.longitude);
            coords.value = [position.coords.latitude, position.coords.longitude];
        });
    }, 1000);
} else {
    /* geolocation IS NOT available */
}
</script>
<template>
    <button class="button is-primary" @click="center = [57.76153605802084, 26.6240710286201]">Go To Litsi</button>
    <button class="button is-primary" @click="center = [59.077307157760046, 24.18202527340709]">Go To Tussu</button>

    <LeafletMap :center="center" :zoom="18" :marker="coords"></LeafletMap>
</template>
