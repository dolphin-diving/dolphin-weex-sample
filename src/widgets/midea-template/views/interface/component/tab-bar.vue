<template>
  <dof-tab-bar
    :tab-titles="tabTitles"
    :tab-styles="tabStyles"
    title-type="icon"
    @dofTabBarCurrentTabSelected="dofTabBarCurrentTabSelected"
  >
    <!-- 第一个页面内容-->
    <div class="item-container" :style="contentStyle">
      <ui-component-page></ui-component-page>
    </div>

    <!-- 第二个页面内容-->
    <div class="item-container" :style="contentStyle">
      <interface-page></interface-page>
    </div>

    <!-- 第三个页面内容-->
    <div class="item-container" :style="contentStyle"><text>模版列表</text></div>
  </dof-tab-bar>
</template>

<script>
import { DofTabBar, Utils } from 'dolphin-weex-ui'
import UiComponentPage from './ui-component'
import InterfacePage from './interface'
import Config from '../config'
export default {
  components: {
    DofTabBar,
    UiComponentPage,
    InterfacePage
  },
  data() {
    return {
      tabTitles: Config.tabIconFontTitles,
      tabStyles: Config.tabIconFontStyles
    }
  },
  created() {
    const tabPageHeight = Utils.env.getPageHeight()
    const { tabStyles } = this
    this.contentStyle = { height: tabPageHeight - tabStyles.height + 'px' }
  },
  methods: {}
}
</script>

<style scoped>
.item-container {
  width: 750px;
  background-color: #f2f3f4;
  align-items: center;
  justify-content: center;
}
</style>
