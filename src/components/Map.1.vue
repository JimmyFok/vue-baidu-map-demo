<template>
  <baidu-map class="map" center="深圳"> 
  </baidu-map>
</template>

<script>

export default {
  name: 'Map',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style>
.map {
  width: 100%;
  height: 300px;
}
</style>