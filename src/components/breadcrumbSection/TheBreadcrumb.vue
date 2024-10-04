<template>
  <section class="col-12 row breadcrumb-section">
    <div class="container col-12">
      <nav aria-label="breadcrumb">
        <ol class="breadcrumb align-items-center">
          <the-breadcrumb-item
            v-for="(page, index) in openedPages"
            :key="`${page}-${index}`"
            :page-name="page"
            :is-current-page="isCurrentPage(page)"
          >
          </the-breadcrumb-item>
        </ol>
      </nav>
    </div>
  </section>
</template>

<script setup>
import TheBreadcrumbItem from '@/components/breadcrumbSection/TheBreadcrumbItem.vue';
import { computed } from 'vue';

const props = defineProps({
  currentPageTitle: {
    type: String,
    default: '',
  },
});

//static data
const openedPages = computed(() => {
  const pages = ['خانه', 'وبلاگ', 'برنامه‌نویسی'];
  if (props.currentPageTitle) {
    pages.push(props.currentPageTitle); // only add currentPageTitle if it's not null
  }
  return pages;
});

// check if the page is the currently open page
const isCurrentPage = (pageName) => pageName === props.currentPageTitle;
</script>
