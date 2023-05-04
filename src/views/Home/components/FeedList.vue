<template>
  <div v-for="item in ArticleList" :key="item.id">
    <Article :article="item"></Article>
  </div>
</template>

<script setup lang="ts">
import markdownToHtml from '../../../utils/markdownToHtml.js'
import MD from 'markdown-it'
import Article from './ArticleCard.vue'
import { ref, onMounted, computed, reactive } from 'vue'
// import test from '../../public/test.md'
import { ArticleAPI } from '../api/api'
const article = ref('')
let md = new MD()
let ArticleList = ref([])

onMounted(async () => {
  let res = await ArticleAPI.GetArticleList()
  ArticleList.value = res.data.data.map((item: any) => {
    item.article_content = md
      .render(item.article_content)
      .replace(/<\/?[^>]*>/g, '')
      .replace(/[|]*\n/, '')
      .replace(/&npsp;/gi, '')
    return item
  })
  console.log('article', ArticleList.value)
})
</script>

<style></style>
