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
      <div slot="right" class="right-img-wrapper">
        <image :src="rightButton" style="height: 40px;width: 40px;"></image>
      </div>
    </dof-minibar>
    <!-- <div :style="{ height: '32px' }"></div> -->
    <div class="tab-bar-wrapper">
      <tab-bar></tab-bar>
    </div>
  </div>
</template>

<script>
import { DofMinibar } from 'dolphin-weex-ui'
import base from 'src/mixins/base'
import TabBar from './components/tab-bar'
export default {
  components: {
    DofMinibar,
    TabBar
  },
  mixins: [base],
  data() {
    return {
      rightButton: './assets/image/header/smart_ic_more_black@2x.png',
      deviceTitle: 'dolphinWeex'
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
.tab-bar-wrapper {
  flex: 1;
}
</style>
