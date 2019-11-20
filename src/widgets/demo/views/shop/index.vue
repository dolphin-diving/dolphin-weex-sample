<template>
  <div class="wrapper">
    <scroller class="main">
      <dof-minibar
        :title="deviceName"
        :left-button="leftButton"
        backgroundColor="#fff"
        :middle-text-style="headerStyle"
        @dofMinibarLeftButtonClicked="minibarLeftButtonClick"
        @dofMinibarRightButtonClicked="minibarRightButtonClick"
      >
        <div slot="right" class="right-img-wrapper">
          <image :src="rightButton" style="height: 36px;width: 36px;"></image>
        </div>
      </dof-minibar>
    </scroller>
  </div>
</template>

<script>
import { DofCell2, DofMinibar } from 'dolphin-weex-ui'

export default {
  components: {
    DofCell2,
    DofMinibar
  },

  data() {
    return {
      rightButton: './assets/image/header/more_gray.png',
      deviceName: '网上商城',
      headerStyle: {
        fontFamily: 'PingFangSC-Regular',
        fontWeight: '900',
        fontSize: '28px',
        letterSpacing: 0,
        color: '#666'
      }
    }
  },
  created() {},

  methods: {}
}
</script>

<style scoped>
.main {
  background-color: #ededee;
  padding-bottom: 200px;
}
</style>
