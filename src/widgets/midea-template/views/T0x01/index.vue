<template>
  <div class="wrapper">
    <dof-minibar
      :title="deviceTitle"
      backgroundColor="transparent"
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
    <scroller>
      <info-panel :state="0" />
      <heater-cell2
        itemImg="./assets/image/temperature.png"
        title="设置温度"
        rightText="60C"
        :hasSubBottomBorder="true"
      />
      <heater-cell2
        itemImg="./assets/image/energy.png"
        title="节能模式"
        desc="一键45C，热量不浪费"
        :hasSwitch="true"
        @clickSwitch="clickSwitch"
        :switchActive="switchActive"
        :hasArrow="false"
        :hasSubBottomBorder="true"
      />
      <heater-cell2
        itemImg="./assets/image/capacity.png"
        title="E+增容"
        desc="突破最高温度限制，提供更多热水"
        :hasSwitch="true"
        @clickSwitch="clickSwitch2"
        :switchActive="switchActive2"
        :hasArrow="false"
      />
      <dof-button
        type="white"
        :btnStyle="{
          width: '750px',
          height: '88px',
          backgroundColor: '#f2f2f2',
          borderRadius: '0px',
          borderWidth: 'none'
        }"
        :textStyle="{ color: '#808080' }"
        @dofButtonClicked="showComp"
        text="展示底部弹窗"
      ></dof-button>
      <heater-confirm-box :inputHeight="670" :show="show" @cancel="cancel">
        <heater-cell
          title="半胆速热"
          desc="快速加热，提供少量热水"
          :isActive="true"
          iconSrc="./assets/img/smart_ic_reline@3x.png"
        />
        <heater-cell
          title="半胆速热"
          desc="快速加热，提供少量热水"
          :isActive="false"
          iconSrc="./assets/img/smart_ic_reline@3x.png"
        />
        <heater-cell title="半胆速热" desc="快速加热，提供少量热水" :isActive="false" />
        <heater-cell title="半胆速热" desc="快速加热，提供少量热水" :isActive="false" />
        <heater-cell title="半胆速热" desc="快速加热，提供少量热水" :isActive="false" />
      </heater-confirm-box>
      <bottom-tab :data="bottomTabAry" />
    </scroller>
    <div style="height:180px;" />
  </div>
</template>

<script>
import { DofCell2, DofMinibar, DofButton } from 'dolphin-weex-ui'
import base from 'src/mixins/base'
import nativeService from 'src/service/nativeService'

import heaterCell2 from '../../component/heater_cell2.vue'
import infoPanel from '../../component/infoPanel.vue'
import heaterCell from '../../component/heater_cell.vue'
import heaterConfirmBox from '../../component/heater_confirmBox.vue'
import bottomTab from '../../component/bottomTab.vue'

export default {
  components: {
    DofCell2,
    DofMinibar,
    DofButton,
    heaterCell2,
    heaterCell,
    infoPanel,
    bottomTab,
    heaterConfirmBox
  },

  data() {
    return {
      leftButton: './assets/image/header/public_ic_back@2x.png',
      rightButton: './assets/image/header/smart_ic_more_black@2x.png',
      deviceTitle: '热水器',
      deviceName: '',
      headerStyle: {
        fontFamily: 'PingFangSC-Regular',
        fontWeight: '900',
        fontSize: '28px',
        letterSpacing: 0
      },
      switchActive: true,
      switchActive2: true,
      show: false,
      bottomTabAry: [
        { srcImg: './assets/image/powerOn.png', text: '关机' },
        { srcImg: './assets/image/yure.png', text: '半胆速热' },
        { srcImg: './assets/image/timing.png', text: '预约' }
      ]
    }
  },
  created() {},

  methods: {
    clickSwitch() {
      this.switchActive = !this.switchActive
    },
    clickSwitch2() {
      this.switchActive2 = !this.switchActive2
    },
    cancel() {
      this.show = false
    },
    showComp() {
      this.show = true
    }
  }
}
</script>

<style scoped>
.wrapper {
  /* background-color: #f2f2f2; */
}
</style>
