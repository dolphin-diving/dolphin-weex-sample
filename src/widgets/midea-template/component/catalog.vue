<template>
  <div class="catalog" :style="{ backgroundColor: bgColor }">
    <text class="text" :style="{ color: textColor }">{{ title }}</text>
  </div>
</template>
<style>
.catalog {
  height: 80px;
  background-color: #a3a380;
  background-color: #9dd3fa;
  background-color: #f6d6ff;
  background-color: #eaf048;
  background-color: #56a36c;
  background-color: #d0e9ff;
  background-color: #eff0dc;
  background-color: #e8cd56;
  background-color: #daf9ca;
  padding-left: 20px;
  justify-content: center;
}
.text {
  font-size: 32px;
}
</style>
<script>
module.exports = {
  props: {
    title: {
      type: String
    },
    bgColor: {
      type: String,
      default: '#daf9ca'
    },
    textColor: {
      type: String,
      default: '#000000'
    }
  }
}
</script>
