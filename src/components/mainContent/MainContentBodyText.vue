<template>
  <!-- eslint-disable -->
  <div
    ref="scrollContainer"
    class="main-content__text--text"
    v-html="sanitizedMainText"
  ></div>
  <!-- eslint-enable -->
</template>

<script setup>
import { computed, nextTick, onMounted, ref } from 'vue';
import { ScrollSpy } from 'bootstrap';
import DOMPurify from 'dompurify';

const props = defineProps({
  mainText: {
    type: String,
    required: true,
  },
});

// Sanitize the HTML content
const sanitizedMainText = computed(() => {
  return DOMPurify.sanitize(props.mainText);
});

// init the scrollspy
const scrollContainer = ref(null);
onMounted(async () => {
  await nextTick();
  setTimeout(() => {
    if (scrollContainer.value) {
      const scrollSpy = new ScrollSpy(scrollContainer.value, {
        target: '#side-bar',
        smoothScroll: true,
        tabindex: 0,
      });
      scrollSpy.refresh();
    }
  });
});
</script>
<style>
.main-content__text--text {
  &:last-child {
    margin-bottom: 0;
  }

  p,
  ul,
  .image {
    margin-bottom: 2rem;
  }

  h2,
  h3 {
    margin-bottom: 1rem;
  }

  a {
    color: #24099a;
  }

  .image {
    width: 100%;
    max-width: 100%;

    img {
      border: 1px solid #dbdbdb;
      width: 100%;
      height: auto;
      object-fit: cover;
    }

    figcaption {
      margin-top: 15px;
      color: #777777;
      text-align: center;
    }
  }
}
</style>
