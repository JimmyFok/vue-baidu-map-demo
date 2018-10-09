<template>
  <baidu-map class="map" :center="{lng: 114.0598, lat: 22.5454}" :zoom="15">
    <bm-marker :position="markerPoint" 
      :dragging="true" animation="BMAP_ANIMATION_BOUNCE" 
      :icon="{url:'../assets/dingwei', size: {width: 300, height: 157}}"
    ></bm-marker>
    <bm-point-collection :points="points" 
     shape="BMAP_POINT_SHAPE_STAR" 
     color="red" 
     size="BMAP_POINT_SIZE_SMALL"
     @click="clickHandler"></bm-point-collection>
  </baidu-map>
</template>

<script>
export default {
  data () {
    return {
      points: [
        {lng: 114.059827, lat: 22.545402},
        {lng: 114.07323, lat: 22.547471}
      ]
    }
  },
  methods: {
    clickHandler (e) {
      alert(`单击点的坐标为：${e.point.lng}, ${e.point.lat}`);
    },
    addPoints () {
      const points = [];
      for (var i = 0; i < 1000; i++) {
        const position = {lng: Math.random() * 40 + 85, lat: Math.random() * 30 + 21}
        points.push(position)
      }
      this.points = points
    }
  }
}
</script>

<style>
.map {
  width: 100%;
  height: 500px;
}
</style>