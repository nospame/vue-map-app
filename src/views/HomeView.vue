<script>
import mapboxgl from 'mapbox-gl';

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
    };
  },
  mounted: function () {
    this.createMap();
  },
  methods: {
    createMap: function () {
      mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_KEY;
      console.log();
      const map = new mapboxgl.Map({
        container: 'map', // container ID
        style: 'mapbox://styles/mapbox/streets-v11', // style URL
        center: [-122.33, 47.61], // starting position [lng, lat]
        zoom: 10,
        pitch: 30,
      });
      map.addControl(new mapboxgl.NavigationControl());
    }
  },
};

;
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div id='map'></div>
  </div>
</template>

<style>
#map {
  height: 400px;
  width: 600px;
}
</style>