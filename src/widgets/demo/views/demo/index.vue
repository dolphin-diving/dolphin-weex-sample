<template>
  <div class="wrapper">
    <dof-minibar
      title="日期模块2"
      backgroundColor="transparent"
      textColor="#404040"
      rightText="More"
      @dofMinibarLeftButtonClicked="minibarLeftButtonClick"
      @dofMinibarRightButtonClicked="minibarRightButtonClick"
    >
    </dof-minibar>
    <div class="show-time">
      {{ testText }}
    </div>
    <scroller class="main">
      <dof-cell2
        v-for="(time, index) in timeList"
        :key="index"
        :title="time.title"
        :desc="time.desc"
        :hasMargin="true"
        :hasArrow="true"
        :clickActivied="true"
        :hasTopBorder="false"
        :hasBottomBorder="false"
        :hasSubBottomBorder="false"
        @dofCellClick="itemClicked"
      >
      </dof-cell2>
    </scroller>
  </div>
</template>

<script>
import moment from 'moment'
// const moment = require('moment')
moment.locale('zh-cn', {
  meridiem: function(hour, minute, isLowercase) {
    if (hour < 9) {
      return '早上'
    } else if (hour < 11 && minute < 30) {
      return '上午'
    } else if (hour < 13 && minute < 30) {
      return '中午'
    } else if (hour < 18) {
      return '下午'
    } else {
      return '晚上'
    }
  }
})
import { DofCell2, DofMinibar } from 'dolphin-weex-ui'

export default {
  components: {
    DofCell2,
    DofMinibar
  },

  data() {
    return {
      time: '2019',
      testText: moment('2019-2-20 13:13:13', 'YYYY-MM-DD hh:mm:ms')
        .startOf('M')
        .format('YYYY-MM-DD hh:mm:ms'),
      timeList: []
    }
  },
  created() {
    this.timeList.splice()
    this.timeList = [
      {
        title: '当前时间:',
        desc: this.dateFormat(new Date())
      },
      {
        title: '测试时间:',
        desc: moment('1995-12-25')
      },
      {
        title: '12-25-1995:',
        desc: moment('12-25-1995', 'MM-DD-YYYY')
      },
      {
        title: '当前时间:',
        desc: moment('29-06-1995', ['MM-DD-YYYY', 'DD-MM-YYYY'], 'fr', true)
      },
      {
        title: '当前时间:',
        desc: moment('2010-01-01T05:06:07', moment.ISO_8601)
      },
      {
        title: '当前时间:',
        desc: moment('2010-01-01T05:06:07', ['YYYY', moment.ISO_8601])
      },
      {
        title: '当前时间-L:',
        desc: moment().format('L')
      },
      {
        title: 'YYYY-MM-DD HH:mm:ss:',
        desc: moment().format('YYYY-MM-DD HH:mm:ss')
      },
      {
        title: '当前时间-LTS:',
        desc: moment().format('LTS')
      },
      {
        title: 'moment({ hour:15, minute:10 }):',
        desc: moment({ hour: 15, minute: 10 })
      },
      {
        title: 'moment([2017, 6, 17]).toNow():',
        desc: moment([2017, 6, 17]).toNow()
      },
      {
        title: 'moment([2019, 10, 29]).fromNow():',
        desc: moment([2019, 10, 29]).fromNow()
      },
      {
        title: 'moment().valueOf()',
        desc: `${moment().valueOf()}: ${new Date().getTime()}: ${+new Date()}  : ${+moment()}`
      },
      {
        title: 'moment().months()',
        desc: moment.months()
      },
      {
        title: 'moment().weekdays()',
        desc: moment.weekdays()
      }
    ]
    let res = this.dateFormat(new Date())
    // this.$MID.alert(`res:${res}`)
    this.time = res
  },

  methods: {
    dateFormat(date) {
      let res
      try {
        res = moment(date).format('YYYY-MM-DD HH:mm:ss')
      } catch (error) {
        this.$MID.alert(error)
      }
      return res
    }
  }
}
</script>

<style scoped></style>
