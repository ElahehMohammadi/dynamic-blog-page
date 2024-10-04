<template>
  <li
    class="breadcrumb-item lh-lg"
    :class="itemStyle"
    :aria-current="ariaCurrent"
  >
    <template v-if="isCurrentPage">{{ pageName }}</template>
    <template v-else>
      <a :href="pageUrl">{{ pageName }}</a>
    </template>
  </li>
  <img
    v-if="!isCurrentPage"
    src="@/assets/img/icons/arrow-left.svg"
    alt="left arrow divider"
    class="icon-xsm"
  />
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  pageName: {
    type: String,
    required: true,
  },
  isCurrentPage: {
    type: Boolean,
  },
});
//style for breadcrumb item based on if it's the current page
const itemStyle = computed(() => {
  return props.isCurrentPage ? 'active title4' : 'sub1';
});
const ariaCurrent = computed(() => {
  return props.isCurrentPage ? 'page' : null;
});
// Implement dynamic URL logic if needed

const pageUrl = computed(() => '#');
</script>
<style lang="scss" scoped>
.breadcrumb-item {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  line-clamp: 1;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
}
</style>
