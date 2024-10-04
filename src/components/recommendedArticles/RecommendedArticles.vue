<template>
  <section class="recommended-articles col-12 row">
    <div class="recommended-articles__container container">
      <div class="recommended-articles__main-heading">
        <heading-with-lines title="مطالب مرتبط"></heading-with-lines>
      </div>
      <div v-if="!relatedBlogsExist" class="d-flex justify-content-center mb-5">
        <p class="w-100 text-center text-gray-dark">مطلب مرتبطی وجود ندارد!</p>
      </div>
      <div v-else class="recommended-articles__carousel">
        <recommended-articles-slider></recommended-articles-slider>
      </div>
    </div>
  </section>
</template>

<script setup>
import RecommendedArticlesSlider from '@/components/recommendedArticles/RecommendedArticlesSlider.vue';
import HeadingWithLines from '@/components/UI/HeadingWithLines.vue';

defineProps({
  relatedBlogsExist: {
    type: Boolean,
    required: true,
  },
});
</script>
