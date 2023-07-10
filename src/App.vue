<template>
  <main>
    <l-map ref="map" v-model:zoom="zoom" v-model:center="center" :useGlobalLeaflet="false">
      <!-- <l-tile-layer url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png'" layer-type="base"
        name="Stadia Maps Basemap"></l-tile-layer> -->
      <l-tile-layer url="https://{s}.google.com/vt/lyrs=s,h&x={x}&y={y}&z={z}" :subdomains="subdomains"></l-tile-layer>
      <!-- <l-tile-layer url="https://tiles.stadiamaps.com/tiles/alidade_smooth_dark/{z}/{x}/{y}{r}.png" layer-type="base"
        name="Stadia Maps Basemap"></l-tile-layer> -->
      <l-marker v-for="arcade in arcades.features" :key="arcade" :lat-lng="arcade.geometry.coordinates.reverse()"></l-marker>
    </l-map>
  </main>+
</template>

<script setup>
import { ref, onMounted } from 'vue'
import "leaflet/dist/leaflet.css"
import { LMap, LTileLayer, LMarker } from "@vue-leaflet/vue-leaflet"

import arcades from "./arcades.json"

const subdomains = ['mt0', 'mt1', 'mt2', 'mt3']

let zoom = ref(6)
let center = ref([38, 139.69])

</script>


<style scoped>
html,
body {
  margin: 0;
  padding: 0;
}

main {
  height: 100vh;
  width: 100vw;
}
</style>
