<template>
  <div class="header">
    <NavBarVue class="nav"></NavBarVue>
  </div>
  <div class="container">
    <el-row v-loading="loading" :gutter="20" justify="center">
      <el-col :span="12" class="article">
        <div class="Tags" v-for="item in article.tagDTOList" :key="item.tag_id">
          <div class="tag_container">
            <div class="tag">{{ item.tag_name }}</div>
          </div>
        </div>
        <div class="Title">{{ article.article_title }}</div>
        <div class="Time">Posted by Hux on {{ article.create_time }}</div>
        <div class="content" v-html="article.article_content"></div>

        <div class="pager">
          <div class="previous" v-if="article?.prevArticle?.article_title">
            <div>PREVIOUS</div>
            <div class="subTitle">{{ article?.prevArticle?.article_title }}</div>
          </div>
          <div class="previous" v-if="article?.lastArticle?.article_title">
            <div>NEXT</div>
            <div class="subTitle">{{ article?.lastArticle?.article_title }}</div>
          </div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>
<script setup lang="ts">
import { onMounted, reactive } from 'vue'
import { useRoute } from 'vue-router'
import NavBarVue from '../../components/NavBar.vue'
import Tags from '../../components/Tags.vue'
import ArticleAPI from '../../api/api.js'
import markdownToHtml from '../../utils/markdownToHtml.js'
import { ref } from 'vue'

const loading = ref(true)
interface Article {
  article_content: string
  create_time: string
  article_title: string
  tagDTOList: []
  prevArticle: PreArticle
  lastArticle: PreArticle
}
interface PreArticle {
  article_title: string
}
const route = useRoute()
let article: Article = reactive({} as Article)
onMounted(async () => {
  const articleId = route.params.id
  const data = await ArticleAPI.GetArticleById(`/articles/${articleId}`)
  article = Object.assign(article, data.data.data)
  article.article_content = markdownToHtml(article.article_content)
  article.create_time = new Date(article.create_time).toDateString()
  loading.value = false
  console.log('article', article)
})
</script>
<style lang="less" scoped>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
.Time {
  font-family: serif;
  font-style: italic;
  font-size: 20px;
  font-weight: lighter;
  line-height: 1.1;
}
.Tags {
  display: flex;
  flex-direction: row;
  border-color: #404040;
}
.nav {
  color: black !important;
  a:link,
  a:visited,
  a:hover,
  a:active {
    color: black !important;
  }
}
.content {
  margin: 30px 0;
  line-height: 1.7;
  font-size: 16px;
  color: #404040;
  -webkit-font-smoothing: antialiased;
  font-weight: 600;
}
.Title {
  font-size: 55px;
  line-height: 1.3;
  margin-top: 10px;
  margin-bottom: 8px;
  font-weight: 700;
  color: #404040;
}
.container {
  margin-top: 100px;
  /* background: #000; */
}
.article {
  /* background: bisque; */
}
.tag_container {
  display: inline-block;
  margin-left: 5px;
}
.tag {
  display: inline-block;
  border: 1px solid rgba(255, 255, 255, 0.8);
  border-color: #404040;
  border-radius: 999em;
  padding: 0 10px 0 10px;
  color: #404040;
  line-height: 24px;
  font-size: 12px;
  text-decoration: none;
  margin: 0 1px;
  margin-bottom: 6px;
  cursor: pointer;
  letter-spacing: 1.5px;
}
.pager {
  margin-top: 40px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.previous {
  border: 1px solid #ddd;
  padding: 20px 30px;
  font-size: 12px;
  font-weight: 800;
  letter-spacing: 1.5px;
  width: 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.subTitle {
  margin-top: 10px;
  color: #a3a3a3;
  font-weight: 400;
  letter-spacing: 0.5px;
}
</style>
