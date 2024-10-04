<template>
  <section class="main-content row">
    <div class="main-content__container container">
      <main-content-body></main-content-body>
      <main-content-sidebar></main-content-sidebar>
    </div>
  </section>
</template>

<script setup>
import MainContentBody from '@/components/mainContent/MainContentBody.vue';
import MainContentSidebar from '@/components/mainContent/MainContentSidebar.vue';
import { nextTick, onMounted, provide, ref } from 'vue';

//get the titles and set id for them
const titles = ref([]);
onMounted(() => {
  nextTick(() => {
    //choose all the contents
    const titleEls = document.querySelectorAll('.main-content__text--text h2');
    titleEls.forEach((title, index) => {
      //get the titles content
      const titleText = title.textContent;
      //set id for the titles
      title.id = `section-${index}`;
      //save the titles content and id
      titles.value.push({
        name: titleText.replace(':', ''),
        id: title.id,
      });
    });
  });
});
provide('titles', titles);
</script>

<style scoped lang="scss">
.main-content {
  &__container {
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: 48px;
    padding-bottom: 40px;
  }

  &__side-bar {
    order: 2;
    flex-grow: 1;
  }
}
</style>
