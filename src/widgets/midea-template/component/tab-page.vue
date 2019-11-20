<template>
  <dof-tab-page
    ref="dof-tab-page"
    :tab-titles="tabTitles"
    :tab-styles="tabStyles"
    title-type="icon"
    :tab-page-height="tabPageHeight"
    @dofTabPageCurrentTabSelected="dofTabPageCurrentTabSelected"
  >
    <div class="slot">
      <list
        v-for="(v, index) in tabList"
        :key="index"
        class="item-container"
        :style="{ height: tabPageHeight - tabStyles.height + 'px' }"
      >
        <cell class="border-cell"></cell>
        <cell v-for="(demo, key) in v" class="cell" :key="key">
          <dof-pan-item
            :ext-id="'1-' + v + '-' + key"
            url="https://h5.m.taobao.com/trip/ticket/detail/index.html?scenicId=2675"
            @dofPanItemPan="dofPanItemPan"
          >
            <div class="content">
              <text>{{ key }}</text>
            </div>
          </dof-pan-item>
        </cell>
      </list>
    </div>
  </dof-tab-page>
</template>
<script>
const dom = weex.requireModule('dom')
import { DofTabPage, DofPanItem, Utils, BindEnv } from 'dolphin-weex-ui'
import Config from './config'

export default {
  components: { DofTabPage, DofPanItem },
  data: () => ({
    tabTitles: Config.tabTitles,
    tabStyles: Config.tabStyles,
    tabList: [],
    pageIndex: 0,
    demoList: [1, 2, 3, 4, 5, 6, 7, 8, 9],
    tabPageHeight: 1334
  }),
  created() {
    this.tabPageHeight = Utils.env.getPageHeight()
    this.tabList = [...Array(this.tabTitles.length).keys()].map(i => [])
    Vue.set(this.tabList, 0, this.demoList)
    // this.$MID.alert(this.tabList)
  },
  methods: {
    dofTabPageCurrentTabSelected(e) {
      const self = this
      const index = e.page
      // this.pageIndex = 0
      this.$MID.alert(e)

      /* Unloaded tab analog data request */
      if (!Utils.isNonEmptyArray(self.tabList[index])) {
        setTimeout(() => {
          Vue.set(self.tabList, index, self.demoList)
        }, 500)
      }
    },
    dofPanItemPan(e) {
      if (BindEnv.supportsEBForAndroid()) {
        this.$refs['dof-tab-page'].bindExp(e.element)
      }
    }
  }
}
</script>
<style scoped>
.item-container {
  width: 750px;
  background-color: #f2f3f4;
}

.border-cell {
  background-color: #f2f3f4;
  width: 750px;
  height: 24px;
  align-items: center;
  justify-content: center;
  border-bottom-width: 1px;
  border-style: solid;
  border-color: #e0e0e0;
}

.cell {
  background-color: #ffffff;
}

.content {
  width: 750px;
  height: 300px;
  border-bottom-width: 1px;
  align-items: center;
  justify-content: center;
}
</style>
