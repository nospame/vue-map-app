<script>
import mapboxgl from 'mapbox-gl';

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      places: [
        { lng: -122.3493, lat: 47.6205, description: "The Space Needle" },
        { lat: 47.6135, lng: 122.3315, description: "The Paramount Theater" }
      ]
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
      // this.places.forEach(function (place) {
      const popup = new mapboxgl.Popup({ offset: 25 }).setText(
        'The Space Needle is 605 feet tall.'
      );
      const el = document.createElement('div');
      el.id = 'marker';
      // })
      new mapboxgl.Marker(el)
        .setLngLat([-122.3493, 47.6205])
        .setPopup(popup) // sets a popup on this marker
        .addTo(map);
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
  margin: auto;
}

#marker {
  background-image: url('https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/SpaceNeedleTopClose.jpg/305px-SpaceNeedleTopClose.jpg');
  background-size: cover;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
}

.mapboxgl-popup {
  max-width: 200px;
}
</style>