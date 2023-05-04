<template>
  <div class="article">
    <div @click="handleClick">
      <div class="title">{{ article.article_title }}</div>
      <div class="content" v-html="article.article_content"></div>
      <div class="post-meta">Posted by Hux on April 10, 2021</div>
    </div>
    <div class="line" />
  </div>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router'
const router = useRouter()
const { article } = defineProps(['article'])
const handleClick = (e: any) => {
  router.push(`/article/${article.id}`)
}
console.log('article', article)
// console.log(markdownToHtml('### test'))
// import MD from 'markdown-it'

// var md = new MD()
// article.value = markdownToHtml(
//   '> 雪碧（doodlewind）邀请我给[《JavaScript 二十年》](https://zhuanlan.zhihu.com/p/373065151) 写的推荐序。' +
//     'JavaScript 常常被戏称为一门偶然成功的玩具语言。而实际上，它出身名门，更是成长在聚光灯之下。纵观历史，有资格被标准化的编程语言甚少，它因此成为多方角力的战场，却也有幸同时得到业界与学界先驱的亲传。时至今日，我们甚至难言是它背负了太多妥协，还是这些妥协才成就了它呢。以史为鉴，或许你会有自己的答案。' +
//     '— 黄玄，Facebook 软件工程师（编程语言、JS 引擎、前端基础设施）、中文前端社区活跃成员。'
// )
// console.log('article', test)
</script>
<style lang="less" scoped>
.article {
  display: flex;
  flex-direction: column;
}
.line {
  margin-top: 20px;
  height: 0.1px;
  background: #a3a3a3;
}

.title {
  font-size: 24px;
  line-height: 1.3;
  margin-top: 30px;
  margin-bottom: 8px;
  &:hover {
    color: #0085a1;
  }
}
.content {
  font-size: 15px;
  font-style: italic;
  color: #a3a3a3;
  line-height: 1.7;
  overflow: hidden;

  text-overflow: ellipsis;

  display: -webkit-box;

  -webkit-line-clamp: 5;

  -webkit-box-orient: vertical;
  &:hover {
    color: #0085a1;
  }
  /* width: 100px; */
}
.post-meta {
  line-height: 1.3;

  font-family: 'Lora', 'Times New Roman', serif;
  color: #a3a3a3;
  font-size: 16px;
  font-style: italic;
  margin-top: 10px;
}
</style>
