<template>
  <div>
    <baidu-map class="map" :center="markerPoint" :zoom="12">
    <!-- 单点 -->
    <bm-marker 
      :position="item.position" 
      :dragging="true" 
      @click="infoWindowOpen" 
      v-for="(item,index) in points"
      :key="index">      
      <!-- <bm-info-window 
        :show="show" 
        :position="item.position" 
        @close="infoWindowClose" 
        @open="infoWindowOpen">
        {{item.msg}}
      </bm-info-window>       -->
    </bm-marker>
    <!-- 海量点 -->
    <!-- <bm-point-collection 
        :points="points" 
        shape="BMAP_POINT_SHAPE_CIRCLE" 
        color="green" 
        size="BMAP_POINT_SIZE_BIG"  
        @click="clickHandler">        
      </bm-point-collection>  -->
    </baidu-map>  
  </div>  
</template>

<script>
export default {
  name: "Map",
  data () {
    return {
      show: false,
      markerPoint: {lng: 113.943083, lat: 22.539636},
      showContent: "我是展示数据",
      points:[
        {
          position: {lng: 114.021199, lat: 22.552821}, 
          msg: "南山分店"
        },
        {
          position: {lng: 113.95494, lat: 22.551919}, 
          msg: "宝安分店"
        },
        {
          position: {lng: 113.885663, lat: 22.58259}, 
          msg: "罗湖分店"
        }
      ]
    }
  },
  methods: {
    infoWindowClose () {
      this.show = false
    },
    infoWindowOpen () {
      this.show = true
    },
    clickHandler (e) {
      alert(`单击点的坐标为：${e.point.lng}, ${e.point.lat}`);
    },
    // addPoints () {
    //   const points = [];
    //   for (var i = 0; i < 1000; i++) {
    //     const position = {lng: Math.random() * 40 + 85, lat: Math.random() * 30 + 21}
    //     points.push(position)
    //   }
    //   this.points = points
    // }
  }
}
</script>

<style>
.map {
  width: 100%;
  height: 500px;
}
</style>