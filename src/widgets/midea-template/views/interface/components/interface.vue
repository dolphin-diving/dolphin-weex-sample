<template>
  <div class="wrapper">
    <scroller>
      <catalog title="bridgeModule"></catalog>
      <dof-cell
        :label="item.label"
        :title="item.name"
        :has-arrow="true"
        @dofCellClick="jumpTo(item.url)"
        :key="`base-${index}`"
        v-for="(item, index) in bridge"
        :has-margin="false"
      ></dof-cell>
    </scroller>
  </div>
</template>

<script>
import { DofCell } from 'dolphin-weex-ui'
import Catalog from '../../../component/catalog'
export default {
  components: {
    DofCell,
    Catalog
  },
  data() {
    return {
      bridge: [
        {
          name: 'goTo',
          label: '页面跳转',
          text: '',
          url: 'goTo.js'
        },
        {
          name: 'apiSpeechModule',
          label: '思必驰语音',
          text: '',
          url: 'apiSpeechModule.js'
        },
        {
          name: 'baiduGeocoder',
          label: '获取位置信息',
          text: '',
          url: 'baiduGeocoder.js'
        },
        {
          name: 'burialPoint',
          label: '美居埋点',
          text: '',
          url: 'burialPoint.js'
        },
        {
          name: 'callTelList',
          label: '打电话',
          text: '',
          url: 'callTelList.js'
        },

        {
          name: 'callTel',
          label: '打电话',
          text: '',
          url: 'callTel.js'
        },
        {
          name: 'chooseMulPhoto',
          label: '多选相片',
          text: '',
          url: 'chooseMulPhoto.js'
        },
        {
          name: 'getDeviceInfor',
          label: '获取当前用户信息',
          text: '',
          url: 'getDeviceInfor.js'
        }
 
      ]
    }
  },

  methods: {
    jumpTo(file) {
      if (file) {
        var url = file
        this.$MID.route.push(url)
      }
    }
  }
}
</script>

<style scoped>
.wrapper {
  width: 750px;
  flex: 1;
}
</style>
