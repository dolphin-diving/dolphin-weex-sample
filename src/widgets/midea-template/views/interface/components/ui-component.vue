<template>
  <div class="wrapper">
    <scroller>
      <catalog title="基础组件"></catalog>
      <dof-cell
        :label="item.label"
        :title="item.name"
        :has-arrow="true"
        @dofCellClick="jumpTo(item.url)"
        :key="`base-${index}`"
        v-for="(item, index) in base"
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
      base: [
        {
          name: '提示(dof-accordion-box)',
          label: 'accordion',
          text: '',
          url: 'accordion.js'
        },
        {
          name: '按钮(dof-button)',
          label: 'button',
          text: '',
          url: 'button.js'
        },
        {
          name: '提示(dof-confirm-box)',
          label: 'confirm',
          text: '',
          url: 'confirm-box.js'
        },

        {
          name: '图片(dof-image)',
          label: 'image',
          text: '',
          url: 'image.js'
        },

        {
          name: '提示(dof-switch)',
          label: 'switch',
          text: '',
          url: 'switch.js'
        }

        // { name: "面板(panel)", label: "panel", text: "", url: "panel-demo.js" },
        // {
        //   name: "滑动菜单(swipe-cell)",
        //   label: "swipe cell",
        //   text: "",
        //   url: "swipe-cell-demo.js"
        // },

        // {
        //   name: "选项卡(tabbar-scroller)",
        //   label: "tabbar",
        //   text: "",
        //   url: "tabbar-scroller-demo.js"
        // },
        // {
        //   name: "选项卡(timeline)",
        //   label: "timeline",
        //   text: "",
        //   url: "timeline-demo.js"
        // }
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
