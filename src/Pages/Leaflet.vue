<script setup>
import * as L from 'leaflet'
import 'leaflet/dist/leaflet.css'
import { onMounted } from 'vue';
import { ref } from 'vue';

onMounted(() => {
    let coords = ref({ lat: 0, lng: 0 });
    let location = null
    if ("geolocation" in navigator) {
        setInterval(() => {
            navigator.geolocation.getCurrentPosition((position) => {
                console.log(position.coords.latitude, position.coords.longitude);
                coords.value.lat = position.coords.latitude;
                coords.value.lng = position.coords.longitude;
                if (location) {
                    location.setLatLng([coords.value.lat, coords.value.lng]).update()
                } else {
                    location = L.marker([coords.value.lat, coords.value.lng]).addTo(map)
                }
            })

        }, 1000);
    } else {
        /* geolocation IS NOT available */
    }

    let map = L.map('map').setView([59.42699949642546, 24.743485211156457], 18);
    L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map);

})


</script>

<template>
    <div id="map"></div>
</template>
<style>
#map {
    height: 800px;
}
</style>