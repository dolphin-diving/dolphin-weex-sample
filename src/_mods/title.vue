<template>
  <div class="dof-title" :aria-hidden="true">
    <!-- <image class="logo" src="https://gw.alicdn.com/tfs/TB1JpgJRFXXXXc7XpXXXXXXXXXX-800-800.png"></image> -->
    <image class="logo" :src="imagePath"></image>
    <text class="text">{{ title }}</text>
  </div>
</template>

<style scoped>
.dof-title {
  flex-direction: row;
  align-items: center;
}

.logo {
  width: 120px;
  height: 120px;
}

.text {
  font-size: 30px;
  font-weight: 600;
  color: #0092d7;
}
</style>

<script>
export default {
  props: {
    title: String,
    src: {
      type: String,
      default: '/assets/image/title.png'
    }
  },
  computed: {
    imagePath() {
      if (this.src !== '') {
        return this._isHttpOrFile(this.src) ? this.src : this._getContext() + this.src
      }
      return null
    }
  },
  methods: {
    _isHttpOrFile(path) {
      return path.indexOf('http') === 0 || path.indexOf('file') === 0
    },
    _getContext() {
      let url = weex.config.bundleUrl
      if (url.indexOf('?') > 0) {
        url = url.substring(0, url.indexOf('?'))
      }
      url = url
        .split('/')
        .slice(0, -1)
        .join('/')
      if (this._isHttpOrFile(url)) {
        return url
      } else {
        if (url.indexOf('/') === 0) {
          url = url.substring(url.indexOf('/') + 1)
        }
        url = `file:///android_asset${url === '' ? '' : '/'}${url}`
      }
      return url
    }
  }
}
</script>
