<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import NavBarVue from './components/NavBar.vue'
import Article from './components/Article.vue'
import Tags from './components/Tags.vue'
import pager from './components/pager.vue'
import About from './components/About.vue'
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
          <Article />
          <Article />
          <Article />
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

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
