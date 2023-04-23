<template>
  <div class="tag_title">FEATURED TAGS</div>
  <div>
    <div class="tag_container"><div class="tag">知乎</div></div>
    <div class="tag_container"><div class="tag">知乎</div></div>
    <div class="tag_container"><div class="tag">知乎</div></div>
    <div class="tag_container"><div class="tag">知乎</div></div>
    <div class="tag_container"><div class="tag">小红书</div></div>
    <div class="tag_container"><div class="tag">小红书</div></div>
    <div class="tag_container"><div class="tag">小红书</div></div>
    <div class="tag_container"><div class="tag">小红书</div></div>
    <div class="line"></div>
  </div>
</template>

<script setup lang="ts"></script>

<style>
.line {
  margin-top: 20px;
  height: 0.1px;
  background: #a3a3a3;
}
.tag_title {
  color: #a3a3a3 !important;
  margin-bottom: 20px;
}
.tag_container {
  display: inline-block;
  margin-left: 5px;
}
.tag {
  display: inline-block;
  border: 1px solid rgba(255, 255, 255, 0.8);
  border-color: #bfbfbf;
  border-radius: 999em;
  padding: 0 10px 0 10px;
  color: #a3a3a3;
  line-height: 24px;
  font-size: 12px;
  text-decoration: none;
  margin: 0 1px;
  margin-bottom: 6px;
  cursor: pointer;
  letter-spacing: 1.5px;
}
</style>
