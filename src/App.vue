<template>
  <div>
    <!--    <div style="margin-top: 1vh;"></div>-->
    <div class="content" style="width: fit-content; " @click="setPoint($event)">
      <img src="@/assets/images/building.jpg" alt="" ref="img" @load="imgWidth = $refs.img.width">
      <div
          class="circle"
          v-for="(point, idx) in points"
          :key="idx"
          :style="`
          width: calc(10px / ${(point.installationWidth / imgWidth)});
          height: calc(10px / ${(point.installationWidth / imgWidth)});
          top: ${(point.y - 4.25) / (point.installationWidth / imgWidth)}px;
          left: ${(point.x - 4.25) / (point.installationWidth / imgWidth)}px;
          `"
      />
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {},
  data() {
    return {
      points: [{"x": 252, "y": 207, "installationWidth": 843}, {"x": 484, "y": 58, "installationWidth": 843}, {
        "x": 651,
        "y": 175,
        "installationWidth": 843
      }, {"x": 593, "y": 135, "installationWidth": 843}, {"x": 553, "y": 115, "installationWidth": 843}, {
        "x": 609,
        "y": 156,
        "installationWidth": 843
      }, {"x": 370, "y": 111, "installationWidth": 843}, {"x": 359, "y": 125, "installationWidth": 843}, {
        "x": 311,
        "y": 153,
        "installationWidth": 843
      }, {"x": 304, "y": 181, "installationWidth": 843}],
      imgWidth: 0,
    }
  },
  methods: {
    setPoint(e) {
      console.log('X', e.layerX)
      console.log('Y', e.layerY)
      console.log(e)
      this.points.push({x: e.layerX, y: e.layerY, installationWidth: this.$refs.img.width})
    }
  },
  computed: {
    get1vh() {
      return window.innerHeight / 100
    },
    get1vw() {
      return window.innerWidth / 100
    },
  },
  mounted() {
    console.log()
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
}

#app {
  height: 100vh;
}

.content {
  height: 100%;
  position: relative;
}

.content img {
  max-width: 100%;
  max-height: 100%;
  margin-right: 15px;
}

.circle {
  background: #000000;
  border-radius: 50%;
  position: absolute;
  z-index: 1;
}
</style>
