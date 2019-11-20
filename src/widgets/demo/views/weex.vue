<template>
  <div class="app-wrapper">
    <scroller class="main">广告中……,3后跳转 </scroller>
  </div>
</template>

<script>
import { DofMinibar } from 'dolphin-weex-ui'
import util from '../util/util'
export default {
  data() {
    return {
      //图片定义
      // leftButton: './assets/image/header/public_back_white.png',
      rightButton: './assets/image/header/cart.png',
      deviceName: '网易严选',
      headerStyle: {
        fontFamily: 'PingFangSC-Regular',
        fontWeight: '900',
        fontSize: '28px',
        letterSpacing: 0,
        color: '#666'
      }
    }
  },
  components: { DofMinibar },
  created() {
    util.initIconFont()
  },
  mounted() {
    setTimeout(() => {
      this.$MID.route.push('home.js')
    }, 3000)
  },
  methods: {
    onTabTo(_result) {}
  }
}
</script>
<style>
body {
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
  color: #333;
}
</style>
<style scoped>
.app-wrapper {
  background-color: #f4f4f4;
}
.main {
  background-color: #ededee;
  padding-bottom: 200px;
}
.r-box {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
</style>
