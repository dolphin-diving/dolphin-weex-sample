<template>
  <div class="wrapper">
    <dof-minibar
      ref="app_bar"
      class="app_bar"
      :title="deviceTitle"
      backgroundColor="#ffffff"
      textColor="#000000"
      :middle-text-style="headerStyle"
      @dofMinibarLeftButtonClicked="minibarLeftButtonClick"
      @dofMinibarRightButtonClicked="minibarRightButtonClick"
    >
      <div slot="left">
        <image :src="leftButton" style="height: 55px;width: 55px;transform:translateX(-10px);"></image>
      </div>
      <div slot="right" class="right-img-wrapper">
        <image :src="rightButton" style="height: 40px;width: 40px;"></image>
      </div>
    </dof-minibar>
    <div :style="{ height: '20px' }"></div>
    <tab-page></tab-page>
    <!-- <catalog title="目录"></catalog> -->
    <!-- <dof-cell2
        :label="item.label"
        :title="item.name"
        :has-arrow="true"
        @dofCellClick="jumpTo(item.url)"
        :key="`layout-${index}`"
        v-for="(item, index) in devices"
        :has-margin="false"
      ></dof-cell2> -->
  </div>
</template>

<script>
import { DofCell2, DofMinibar } from 'dolphin-weex-ui'
import base from 'src/mixins/base'
import Catalog from '../../component/catalog'
import TabPage from '../../component/tab-page'
export default {
  components: {
    DofCell2,
    DofMinibar,
    Catalog,
    TabPage
  },
  mixins: [base],
  data() {
    return {
      leftButton: './assets/image/header/public_ic_back@2x.png',
      rightButton: './assets/image/header/smart_ic_more_black@2x.png',
      deviceTitle: 'weex app接口列表',
      deviceName: '',
      devices: [
        {
          name: '动效(lottery)',
          label: 'lottery',
          text: '',
          url: 'lottery-view.js'
        }
      ],
      business: [
        {
          name: '美居(业务页面)',
          label: '智能灯主功能',
          text: '',
          url: 'meijv-intelligent-lamp.js'
        }
      ]
    }
  },
  created() {},

  methods: {
    minibarRightButtonClick() {
      this.reload()
    }
  }
}
</script>

<style scoped>
.wrapper {
  background-color: #f2f2f2;
}
.main {
  padding-top: 20px;
}
</style>
