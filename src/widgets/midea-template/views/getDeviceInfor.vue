<template>
  <div class="wrapper">
    <dof-minibar
      ref="app_bar"
      class="app_bar"
      :title="deviceTitle"
      backgroundColor="#ffffff"
      textColor="#000000"
      @dofMinibarRightButtonClicked="minibarRightButtonClick"
    >
      <div slot="right" class="right-img-wrapper">
        <image :src="rightButton" style="height: 40px;width: 40px;"></image>
      </div>
    </dof-minibar>
    <catalog title="代码"></catalog>
    <div class="main">
      <dof-button text="执行getDeviceInfo" type="primary" @dofButtonClicked="excuteClicked"></dof-button>
      <text class="display-block">
        nativeService.getDeviceInfo().then( (resp) => { this.result = resp } ).catch((error) => {
        nativeService.toast(error) })
      </text>
    </div>
    <catalog title="结果"></catalog>
    <scroller class="result-wrapper">
      <text class="display-block">{{ result ? '返回类型:' + typeof result : '' }}</text>
      <text class="display-block">{{ result }}</text>
    </scroller>
  </div>
</template>
<style scoped>
.wrapper {
  width: 750px;
}
.main {
  align-items: center;
  padding-top: 32px;
  padding-bottom: 32px;
}
.result-wrapper {
  width: 750px;
  align-items: flex-start;
  justify-content: flex-start;
}
.display-block {
  font-size: 30px;
  padding-left: 10px;
  padding-right: 10px;
  padding-top: 10px;
  padding-bottom: 10px;
  background-color: bisque;
  margin-top: 20px;
}
</style>
<script>
import { DofMinibar, DofButton } from 'dolphin-weex-ui'
import base from 'src/mixins/base'
import nativeService from 'src/service/nativeService'
import Catalog from '../component/catalog'

module.exports = {
  components: { DofMinibar, DofButton, Catalog },
  mixins: [base],
  data() {
    return {
      deviceTitle: 'getDeviceInfor',
      rightButton: './assets/image/header/smart_ic_more_black@2x.png',
      result: ''
    }
  },
  methods: {
    excuteClicked() {
      nativeService
        .getDeviceInfo()
        .then(resp => {
          this.result = resp
        })
        .catch(error => {
          nativeService.toast(error)
        })
    },
    minibarRightButtonClick() {
      this.reload()
    }
  },
  created() {}
}
</script>
