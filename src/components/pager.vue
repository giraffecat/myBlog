<template>
  <div class="pager">
    <div class="previous">&larr; NEWER POSTS</div>
    <div class="previous">OLDER POSTS &rarr;</div>
  </div>
</template>

<script setup lang="ts"></script>

<style>
.pager {
  margin-top: 40px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.previous {
  border: 1px solid #ddd;
  padding: 20px;
  font-size: 12px;
  font-weight: 800;
  letter-spacing: 1.5px;
}
</style>
