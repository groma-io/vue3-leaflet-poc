<template>
    <div id='map'>
      <div id="mapid" v-bind:style="mapid"></div>
    </div>
</template>

<script>
export default {
  name: 'Map',
  data() {
      return {
        mapid: {
          height: '750px',
          width: '750px'
        }
      }
    },
  mounted() {
      var mymap = L.map('mapid').setView([41.712520865544, -93.79242334094275], 17); /*global L*/

      L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoiYnJ5YW5naWxsIiwiYSI6ImNramFkamRtNzQ0dGYycW0wbHZ6eTltejgifQ.jo9yzBOY_gklURg2piqzLg', {
        attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
        maxZoom: 18,
        id: 'mapbox/satellite-v9',
        tileSize: 512,
        zoomOffset: -1,
        accessToken: 'pk.eyJ1IjoiYnJ5YW5naWxsIiwiYSI6ImNramFkamRtNzQ0dGYycW0wbHZ6eTltejgifQ.jo9yzBOY_gklURg2piqzLg'
      }).addTo(mymap);

      // var polygon = L.polygon([
      //   [51.509, -0.08],
      //   [51.503, -0.06],
      //   [51.51, -0.047]
      // ]).addTo(mymap);

      mymap.pm.addControls({
        position: 'topleft',
        // drawCircle: false,
      });
    },
  
//   props: {
//     msg: String
//   }
}
</script>
<style scoped>
  #map {
    height: 100%;
    width: 100%;
  }
</style>