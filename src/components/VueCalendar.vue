<template>
  <div>
    <p>Here comes the Web Component</p>
    <map-route :destination="destination" :style="{height:mapheight+'px'}"
               :apikey="apikey"
               :uiLayer="uilayer"
               :origin="origin"
               :lineColor="linecolor"
               :markerIcon="markericon"
               :maplayer="maplayer">
    </map-route>
  </div>
</template>

<script>
export default {
  name: 'VueRoute',
  props: {
    destination: {
      type: String,
      required: true,
    },
    apikey: {
      type: String,
      required: true,
    },
    mapheight: {
      type: Number,
      default: 500,
    },
    uilayer: {
      type: Boolean,
      default: false,
    },
    linecolor: {
      type: String,
      default: undefined,
    },
    origin:{
      type:String,
      default: undefined,
    },
    markericon:{
      type:String,
      default: undefined,
    },
    maplayer:{
      type:String,
      default:"normal"
    }
}}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
