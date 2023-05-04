<template>
  <div ref="getHeigh" :class="navStyle">
    <div class="nav-container">
      <div class="navbar-brand">
        <router-link to="/"> HUI BLOG</router-link>
      </div>
      <div style="flex-grow: 1"></div>
      <div class="nav-item">
        <div>
          <router-link to="/"> HOME </router-link>
        </div>
        <div>ABOUT</div>
        <div>ARCHIVE</div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, computed } from 'vue'
const getHeigh = ref()
const activeIndex = ref('1')
const preScrollTop = ref(0)
const isShow = ref(true)
const navStyle = computed(() => {
  if (preScrollTop.value == 0) {
    return 'navbar'
  } else if (isShow.value) {
    return 'navbar is-fixed'
  } else {
    return 'navbar is-fixed is-visible'
  }
})
const handleSelect = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
onMounted(() => {
  console.log('getHeigh', getHeigh.value)
})

onMounted(() => {
  window.addEventListener('scroll', scrolltop, true)
})

const scrolltop = () => {
  // console.log('scrolltop', preScrollTop.value)

  let scroll = document.documentElement.scrollTop || document.body.scrollTop
  if (preScrollTop.value < scroll) {
    isShow.value = true
  } else {
    isShow.value = false
  }
  preScrollTop.value = scroll
}
</script>

<style lang="less">
@brand-primary: #01a6c7;
.navbar {
  /* background: none;
  border: none; */
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 3;
  color: white;

  /* Hux learn from
     *     TypeIsBeautiful,
     *     [This Post](http://zhuanlan.zhihu.com/ibuick/20186806) etc.
     */
  font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', 'Arial', 'PingFang SC',
    'Hiragino Sans GB', 'STHeiti', 'Microsoft YaHei', 'Microsoft JhengHei', 'Source Han Sans SC',
    'Noto Sans CJK SC', 'Source Han Sans CN', 'Noto Sans SC', 'Source Han Sans TC',
    'Noto Sans CJK TC', 'WenQuanYi Micro Hei', SimSun, sans-serif;
  line-height: 1.7;
  -webkit-transition: background-color 0.3s;
  -moz-transition: background-color 0.3s;
  transition: background-color 0.3s;
  a {
    &:hover,
    &:focus {
      color: @brand-primary;
    }
  }
}
.nav-container {
  display: flex;
  flex-direction: row;
  align-items: center;
}
.navbar-brand {
  padding: 20px;
  line-height: 20px;
  font-weight: 900;
  letter-spacing: 1px;
}

.nav-item {
  display: flex;
  flex-direction: row;
  margin-right: 20px;
  font-size: 12px;
  font-weight: 600;
}
.nav-item > div {
  padding: 20px;
  /* padding-bottom: 10px; */
  line-height: 20px;
  letter-spacing: 1px;
}
.is-visible {
  /* if the user changes the scrolling direction, we show the header */
  -webkit-transform: translate3d(0, 100%, 0);
  -moz-transform: translate3d(0, 100%, 0);
  -ms-transform: translate3d(0, 100%, 0);
  -o-transform: translate3d(0, 100%, 0);
  transform: translate3d(0, 100%, 0);
}
.is-fixed {
  /* when the user scrolls down, we hide the header right above the viewport */
  position: fixed;
  top: -61px;
  background-color: rgba(255, 255, 255, 0.9);
  color: #404040;
  border-bottom: 1px solid #f2f2f2;
  -webkit-transition: -webkit-transform 0.3s;
  -moz-transition: -moz-transform 0.3s;
  transition: transform 0.3s;
  a {
    color: #404040 !important;
  }
}
</style>
