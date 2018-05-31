<template>
  <div>
    <div style="height: 10%; overflow: auto;">
      <h3>Simple map</h3>
      Marker is placed at {{ marker.lat }}, {{ marker.lng }}
    </div>
    <l-map style="height: 90%" :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker :lat-lng="marker"></l-marker>
    </l-map>
  </div>
</template>

<script>
import { LMap, LTileLayer, LMarker } from 'vue2-leaflet'
import L from 'leaflet'

export default {
  name: 'example',
  components: {
    LMap,
    LTileLayer,
    LMarker
  },
  data () {
    return {
      zoom: 13,
      center: L.latLng(54.643307, -6.744371),
      url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
      attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      marker: L.latLng(54.643307, -6.744371)
    }
  },
  mounted: function () {
    setTimeout(function () { window.dispatchEvent(new Event('resize')) }, 250)
  }
}
</script>
