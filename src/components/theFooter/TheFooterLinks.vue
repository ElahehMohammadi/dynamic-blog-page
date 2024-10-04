<template>
  <div class="col-lg-2 col-sm-4 col-5 links" :class="'links--' + linkName">
    <span class="title3 lh-lg">{{ linksTitle }}</span>
    <div class="links-container">
      <!-- links -->
      <span v-for="item in links" :key="item" class="sub1">
        {{ item }}
      </span>
    </div>
  </div>
</template>

<script setup>
defineProps({
  linksTitle: {
    type: String,
    required: true,
  },
  linkName: {
    type: String,
    required: true,
  },
  links: {
    type: Array,
    required: true,
  },
});
</script>
