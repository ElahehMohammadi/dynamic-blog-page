<template>
  <div class="main-content__text">
    <main-content-body-text
      :main-text="blogData.article.text"
    ></main-content-body-text>
    <main-content-body-tags :tags="blogData.tags"></main-content-body-tags>
  </div>
</template>

<script setup>
import MainContentBodyText from '@/components/mainContent/MainContentBodyText.vue';
import MainContentBodyTags from '@/components/mainContent/MainContentBodyTags.vue';
import { inject } from 'vue';

const blogData = inject('blogData');
</script>
<style>
.main-content__text {
  @media (max-width: 992px) {
    gap: 40px;
  }
  gap: 60px;
  order: 1;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}
</style>
