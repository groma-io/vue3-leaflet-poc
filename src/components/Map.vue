<template>
    <div id='map'>
      <p>Enter access token:</p>
      <input id='mapToken' type="text" v-model="map_arguments.accessToken"><button @click='updateMap'>load map</button>
      <div id="mapid" v-bind:style="mapid"></div>
    </div>
</template>

<script>
export default {
  name: 'Map',
  data() {
      return {
        tile: null,
        map: null,
        mapid: {
          height: '750px',
          width: '750px'
        },
        map_arguments: {
          maxZoom: 18,
          id: 'mapbox/satellite-v9',
          tileSize: 512,
          zoomOffset: -1,
          accessToken: '',
          attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
          
        }
      }
    },
  mounted() {
    
    },
    computed() {

    },
    
    updated() {
      // this.tile.setUrl('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=' + this.map_arguments.accessToken, true)
    },
    
    methods: {
      updateMap: function() {
      
      if (this.tile === null) {
        this.map = L.map('mapid').setView([41.712520865544, -93.79242334094275], 17); /*global L*/
        
        this.tile = L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=' + this.map_arguments.accessToken, {
          attribution: this.map_arguments.attribution,
          maxZoom: this.map_arguments.maxZoom,
          id: this.map_arguments.id,
          tileSize: this.map_arguments.tileSize,
          zoomOffset: this.map_arguments.zoomOffset,
        })
        
        this.tile.addTo(this.map);
  
        this.map.pm.addControls({
          position: 'topleft',
          // drawCircle: false,
        });
      } else {
        this.tile.setUrl('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=' + this.map_arguments.accessToken, false)
      }

        
        }
    }

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
  #mapToken {
    margin-bottom: 20px;
    margin-right: 10px;
  }
</style>