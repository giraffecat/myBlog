<script setup lang="ts">
import TheWelcome from '../../components/TheWelcome.vue'
import { RouterLink, RouterView } from 'vue-router'
import NavBarVue from '../../components/NavBar.vue'
import Article from './components/ArticleCard.vue'
import Tags from '../../components/Tags.vue'
import pager from '../../components/pager.vue'
import About from '../../components/About.vue'
import feedList from './components/FeedList.vue'
</script>

<template>
  <header class="header">
    <NavBarVue></NavBarVue>
    <div class="blog_title">
      <div>Hui Blog</div>
      <div class="sub_title">「离开世界之前 一切都是过程」</div>
    </div>
  </header>
  <div class="container">
    <el-row :gutter="20" class="article_list">
      <el-col :span="12" :offset="4">
        <div class="dark">
          <feedList></feedList>
        </div>
        <pager />
      </el-col>
      <el-col :span="4" class="sideBar"
        ><div>
          <Tags />
          <About /></div
      ></el-col>
    </el-row>
  </div>
</template>

<style scoped>
.header {
  position: relative;
  /* line-height: 1.5;
  height: 100; */
  height: 500px;
  background-image: url('src/assets/home-bg.jpg');
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin-bottom: 50px;
}
.sideBar {
  margin-left: 80px;
}
.container {
  height: 1200px;
  /* background: grey; */
}
.article_list {
  height: 300px;
}
.blog_title {
  font-size: 80px;
  color: white;
}
.sub_title {
  font-size: 18px;
  font-weight: 100;
  padding: 15px;
}
</style>
