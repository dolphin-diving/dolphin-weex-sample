<template>
  <div class="flex-column center">
    <dof-image src="/assets/image/logo.png" width="150px" height="150px"></dof-image>
    <text class="h2">插件开发示例</text>
    <text class="h4 margin-top-40 margin-bottom-20">Midea 模版项目</text>
    <dof-button text="快速查看" type="primary" size="big" @dofButtonClicked="jumpTo"></dof-button>
    <div class="footer">
      <text class="copyright">&copy;Midea IOT software</text>
    </div>
  </div>
</template>
<script>
import { DofImage, DofButton } from 'dolphin-weex-ui'
import nativeService from 'src/service/nativeService'
const globalEvent = weex.requireModule('globalEvent')

module.exports = {
  components: {
    DofButton,
    DofImage
  },
  data: function() {
    return {
      messageParam: {
        desiredAccuracy: '10', //定位的精确度
        distanceFilter: '10', //移动多少米回调一次定位信息，
        alwaysAuthorization: '0' //是否需要一直定位, 0:不一直定位，1：一直定位
      },
      result: ''
    }
  },
  methods: {
    jumpTo() {
      // this.linkapi.getLoginInfo((res) => {
      //     this.$alert(11);
      //     this.$alert(res);
      //     let user = [];
      //     user.push(res.userId);
      //     let ss = {
      //         pickUsers: 0,
      //         groupName: "333",
      //         isPublic: 1
      //     };
      //     this.$alert(ss);
      //     this.linkapi.createGroup(ss, (resp) => {
      //         this.$alert("suc");
      //         this.$alert(resp);
      //     }, (error) =>{
      //         this.$alert("error");
      //         this.$alert(error);
      //     });
      // });
      // const welcome = 'welcome to preview page!'
      // this.$MID.toast(welcome, 2)
      var url = 'weex.js'
      this.$MID.route.push(url)
    }
  },
  created() {
    nativeService
      .getGPSInfo(this.messageParam)
      .then(resp => {
        this.result = resp
        this.$MID.alert(resp)
      })
      .catch(error => {
        this.result = 'error: ' + JSON.stringify(error || {})
      })
  },
  mounted: function() {
    globalEvent.addEventListener('androidback', e => {
      this.$pop()
    })
  }
}
</script>

<style scoped>
.footer {
  position: absolute;
  bottom: 10px;
  right: 20px;
}
.copyright {
  font-size: 20px;
  color: #464c5b;
}
.margin-top-40 {
  margin-top: 40px;
}
.margin-bottom-20 {
  margin-bottom: 20px;
}
.flex-row {
  flex-direction: row;
}

.flex-column {
  flex-direction: column;
}

.flex-fluid {
  flex-wrap: wrap;
}

.center {
  justify-content: center;
  align-items: center;
}

.column-center-top {
  align-items: center;
}

.column-center-bottom {
  justify-content: flex-end;
  align-items: center;
}

.column-center-left {
  justify-content: center;
  align-items: flex-start;
}

.column-center-right {
  justify-content: center;
  align-items: flex-end;
}

.column-left-top {
  justify-content: flex-start;
  align-items: flex-start;
}

.column-right-top {
  justify-content: flex-start;
  align-items: flex-end;
}

.column-left-bottom {
  justify-content: flex-end;
  align-items: flex-start;
}

.column-right-bottom {
  justify-content: flex-end;
  align-items: flex-end;
}

.row-space-between {
  justify-content: space-between;
  align-items: center;
}

.row-center-top {
  justify-content: center;
  align-items: flex-start;
}

.row-center-bottom {
  justify-content: center;
  align-items: flex-end;
}

.row-center-left {
  justify-content: flex-start;
  align-items: center;
}

.row-center-right {
  justify-content: flex-end;
  align-items: center;
}

.row-left-top {
  justify-content: flex-start;
  align-items: flex-start;
}

.row-right-top {
  justify-content: flex-end;
  align-items: flex-start;
}

.row-left-bottom {
  justify-content: flex-start;
  align-items: flex-end;
}

.row-right-bottom {
  justify-content: flex-end;
  align-items: flex-end;
}

.span1 {
  flex: 1;
}

.span2 {
  flex: 2;
}

.span3 {
  flex: 3;
}

.span4 {
  flex: 4;
}

.span5 {
  flex: 5;
}

.span6 {
  flex: 6;
}

.span7 {
  flex: 7;
}

.span8 {
  flex: 8;
}

.span9 {
  flex: 9;
}

.span10 {
  flex: 10;
}

.span11 {
  flex: 11;
}

.span12 {
  flex: 12;
}

.flex1 {
  flex: 1;
}

.flex2 {
  flex: 2;
}

.flex3 {
  flex: 3;
}

.flex4 {
  flex: 4;
}

.flex5 {
  flex: 5;
}

.flex6 {
  flex: 6;
}

.flex7 {
  flex: 7;
}

.flex8 {
  flex: 8;
}

.flex9 {
  flex: 9;
}

.flex10 {
  flex: 10;
}

.flex11 {
  flex: 11;
}

.flex12 {
  flex: 12;
}

.p-a {
  position: absolute;
}

.badges {
  background-color: #ff4e24;
  width: 50px;
  height: 40px;
  border-radius: 30px;
  text-align: center;
  color: #ffffff;
  padding-top: 7px;
  font-size: 24px;
}

.large-badges {
  background-color: #ff4e24;
  width: 70px;
  height: 40px;
  border-radius: 30px;
  text-align: center;
  color: #ffffff;
  padding-top: 7px;
}

.bgRed {
  background-color: #fa3300;
}

.h1 {
  font-size: 80px;
  line-height: 120px;
  color: #464c5b;
}

.h2 {
  font-size: 60px;
  line-height: 100px;
  color: #464c5b;
}

.h3 {
  font-size: 45px;
  line-height: 60px;
  color: #464c5b;
}

.h4 {
  font-size: 32px;
  line-height: 45px;
  color: #464c5b;
}

.h5 {
  font-size: 28px;
  line-height: 40px;
  color: #464c5b;
}
</style>
