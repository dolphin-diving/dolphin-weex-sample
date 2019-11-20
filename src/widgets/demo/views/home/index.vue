<template>
  <div class="wrapper">
    <home-header></home-header>
    <top-channel></top-channel>
    <scroller
      :class="['main-list', isIpx && isIpx() ? 'ml-ipx' : '']"
      offset-accuracy="300"
      loadmoreoffset="300"
      @loadmore="onloadmore"
    >
      <refresher @loadingDown="loadingDown"></refresher>
      <div class="cell-button" @click="jumpWeb('https://m.you.163.com/act/pub/DxDpYNfbBd.html')">
        <yx-slider :imageList="YXBanners"></yx-slider>
        <div class="slogan">
          <text class="i-slg iconfont">&#xe63a; 网易自营品牌</text>
          <text class="i-slg iconfont">&#xe63a; 30天无忧退货</text>
          <text class="i-slg iconfont">&#xe63a; 48小时快速退款</text>
        </div>
      </div>
      <!-- <div class="cell-button">
        <block-1 :title="makers.title" :items="makers.items"></block-1>
      </div>
      <div class="cell-button">
        <block-2 hasMore="true" newGoods="true" :head="recommend.head1" :goods="recommend.goods1"></block-2>
      </div>
      <div class="cell-button">
        <block-2 hasMore="true" hotGoods="true" :head="recommend.head2" :goods="recommend.goods2"></block-2>
      </div>
      <div class="cell-button">
        <block-3 :goods="goodsList"></block-3>
      </div> -->
      <loading class="loading" @loading="onloading" :display="showLoading">
        <text class="indicator">...</text>
      </loading>
    </scroller>
    <tab-bar @tabTo="onTabTo" ref="tabBar"></tab-bar>
  </div>
  <!-- <div class="app-wrapper">
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
    <tab-bar @tabTo="onTabTo" ref="tabBar"></tab-bar>
  </div> -->
</template>

<script>
import { DofMinibar } from 'dolphin-weex-ui'
import tabBar from '../../component/tabBar.vue'
import util from '../../util/util'
var modal = weex.requireModule('modal')
var navigator = weex.requireModule('navigator')
// import util from '../util';
import HomeHeader from '../../component/Header.vue'
import refresher from '../../component/refresh.vue'
import topChannel from '../../component/topChannel.vue'
import YXSlider from '../../component/YXSlider.vue'
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
  components: { HomeHeader, refresher, topChannel, YXSlider, tabBar },
  created() {
    util.initIconFont()
  },
  mounted() {
    // setTimeout(() => {
    //   this.$MID.route.push('home.js')
    // }, 3000)
  },
  methods: {
    onTabTo(_result) {
      // this.$MID.alert(_result)
      // let _key = _result.data.key || '';
      // this.$router && this.$router.push('/'+_key)
      let {
        data: { key }
      } = _result
      if (key && key === 'home') {
        this.$MID.route.push('home.js')
      } else if (key && key === 'topic') {
        this.$MID.route.push('topic.js')
      } else if (key && key === 'class') {
        this.$MID.route.push('class.js')
      } else if (key && key === 'shop') {
        this.$MID.route.push('shop.js')
      } else if (key && key === 'my') {
        this.$MID.route.push('my.js')
      }
    },
    minibarRightButtonClick() {
      this.$MID.route.push('shop.js')
    }
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
.iconfont {
  font-family: iconfont;
}
.wrapper {
}
.main-list {
  position: fixed;
  top: 168px;
  bottom: 90px;
  left: 0;
  right: 0;
  /*margin-top: 167px;*/
  /*margin-bottom: 90px;*/
}
.ml-ipx {
  top: 208px;
  bottom: 140px;
}

.cell-button {
  padding-bottom: 18px;
}
.slogan {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  background-color: #fff;
}
.i-slg {
  height: 66px;
  font-size: 26px;
  padding-top: 16px;
  flex: 1;
  text-align: center;
  color: #b4282d;
}
</style>
