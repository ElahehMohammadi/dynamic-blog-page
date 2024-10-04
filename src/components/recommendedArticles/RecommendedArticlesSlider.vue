<template>
  <swiper
    ref="swiperInstance"
    :slides-per-view="1"
    :space-between="0"
    :loop="true"
    class="carousel"
    @swiper="onSwiper"
  >
    <swiper-slide
      v-for="(chunk, index) in chunkedRelatedBlogsData"
      :key="index"
    >
      <div class="d-flex flex-row gap-3">
        <recommended-articles-slider-article
          v-for="article in chunk"
          :key="article"
          :blog-data="article"
        ></recommended-articles-slider-article>
      </div>
    </swiper-slide>
    <div class="swiper-nav-pagination">
      <button class="btn swiper-button-prev" @click="goPrev">
        <img
          src="@/assets/img/icons/arrow-right-2.svg"
          alt="right arrow"
          class="icon-lg"
        />
      </button>
      <div
        class="swiper-pagination swiper-pagination-clickable swiper-pagination-bullets swiper-pagination-horizontal"
      >
        <span
          v-for="(_, index) in chunkedRelatedBlogsData"
          :key="index"
          class="swiper-pagination-bullet"
          :class="
            index === chosenIndex ? 'swiper-pagination-bullet-active' : ''
          "
          @click="gotoSlide(index)"
        ></span>
      </div>
      <button class="btn swiper-button-next" @click="goNext">
        <img
          src="@/assets/img/icons/arrow-left-2.svg"
          alt="left arrow"
          class="icon-lg"
        />
      </button>
    </div>
  </swiper>
</template>

<script setup>
//////////// SECTION //imports
import RecommendedArticlesSliderArticle from '@/components/recommendedArticles/RecommendedArticlesSliderArticle.vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';
import 'swiper/css/pagination';
import { computed, inject, onBeforeMount, onBeforeUnmount, ref } from 'vue';

//get the fetched data
const relatedBlogsData = inject('relatedBlogsData');

//////////// SECTION // chunk the articles to slides based on the window size
let articlesPerSlide = ref(null);
const SCREEN_BREAKPOINTS = {
  SMALL: 768,
  MEDIUM: 992,
};
const currentWindowSize = ref('');

/// SUB SECTION  //chunk the array
function chunkArray(array, chunkSize) {
  const chunks = [];
  let chunk = [];

  array.forEach((item, index) => {
    chunk.push(item);

    //reached the chuck size or the end of array
    if ((index + 1) % chunkSize === 0 || index === array.length - 1) {
      chunks.push(chunk);
      chunk = []; // reset for the next chunk
    }
  });
  return chunks;
}

const chunkedRelatedBlogsData = computed(() => {
  return chunkArray(relatedBlogsData.value, articlesPerSlide.value || 1);
});
/// SUB SECTION //get the articles per slide based on the window
const getWindowSize = () => {
  const screenWidth = window.innerWidth;
  if (screenWidth < SCREEN_BREAKPOINTS.SMALL) return 'phone';
  if (screenWidth < SCREEN_BREAKPOINTS.MEDIUM) return 'tablet';
  return 'desktop';
};
const updateSlides = () => {
  const newWindowSize = getWindowSize();
  if (newWindowSize === currentWindowSize.value) return;
  if (newWindowSize === 'phone') articlesPerSlide.value = 1;
  if (newWindowSize === 'tablet') articlesPerSlide.value = 2;
  if (newWindowSize === 'desktop') articlesPerSlide.value = 3;
  currentWindowSize.value = newWindowSize;
};
// debounce the resize event to prevent frequent updates
const debouncedUpdateSlides = () => {
  clearTimeout(window.resizeTimeout);
  window.resizeTimeout = setTimeout(updateSlides, 100);
};

onBeforeMount(() => {
  updateSlides(); //set the init slide number
  window.addEventListener('resize', debouncedUpdateSlides); // listen for resize events
});

onBeforeUnmount(() => {
  window.removeEventListener('resize', debouncedUpdateSlides); // cleanup event listener
});

//////////// SECTION //slider functions
const swiperInstance = ref(null);
const chosenIndex = ref(0);

const onSwiper = (swiper) => {
  swiperInstance.value = swiper;
  swiper.on('slideChange', () => {
    chosenIndex.value = swiper.realIndex;
  });
};

const goNext = () => swiperInstance.value?.slideNext();
const goPrev = () => swiperInstance.value?.slidePrev();
const gotoSlide = (index) => {
  chosenIndex.value = index;
  swiperInstance.value?.slideToLoop(index);
};
</script>
