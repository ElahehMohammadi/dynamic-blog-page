<template>
  <the-header></the-header>
  <the-breadcrumb :current-page-title="blogData?.title"></the-breadcrumb>
  <div v-if="isLoading || isLoadFailed">
    <the-status-indicator
      :is-load-failed="isLoadFailed"
      :is-loading="isLoading"
    ></the-status-indicator>
  </div>
  <main v-else class="col-12">
    <the-hero></the-hero>
    <main-content></main-content>
    <recommended-articles
      :related-blogs-exist="relatedBlogsExist"
    ></recommended-articles>
    <the-author-card></the-author-card>
    <comments-section></comments-section>
  </main>
  <the-footer></the-footer>
</template>

<script setup>
//////////// SECTION import the components
import TheHeader from '@/components/theHeader/TheHeader.vue';
import TheBreadcrumb from '@/components/breadcrumbSection/TheBreadcrumb.vue';
import TheStatusIndicator from '@/components/UI/TheStatusIndicator.vue';
import TheFooter from '@/components/theFooter/TheFooter.vue';
import CommentsSection from '@/components/commentsSection/CommentsSection.vue';
import RecommendedArticles from '@/components/recommendedArticles/RecommendedArticles.vue';
import TheHero from '@/components/theHero/TheHero.vue';
import MainContent from '@/components/mainContent/MainContent.vue';
import TheAuthorCard from '@/components/authorCard/TheAuthorCard.vue';
import { onBeforeMount, provide, ref } from 'vue';
import axios from 'axios';
//////////// SECTION global func and var
const URL = {
  BLOG: 'https://api.sokanacademy.com/api/blogs/8-common-data-structures-every-programmer-must-know',
  RELATED_BLOGS: 'https://api.sokanacademy.com/api/related',
};

const fetchData = async (url, params) => {
  try {
    const { data } = await axios.get(url, { params: params });
    return data.data;
  } catch (error) {
    console.error(`network error: ${error}`);
    throw error;
  }
};

//////////// SECTION  //get the blog data from api
const isLoading = ref(true);
const blogData = ref(null);
const isLoadFailed = ref(false);
onBeforeMount(async function () {
  try {
    blogData.value = await fetchData(URL.BLOG, {});

    isLoading.value = false;
  } catch (error) {
    isLoading.value = false;
    isLoadFailed.value = true;
    console.error(`Failed to fetch data from url: ${error.message}`);
  }
});
provide('blogData', blogData);

//////////// SECTION //get the related blogs data from api
const relatedBlogsData = ref(null);
const relatedBlogsExist = ref(false);
const relatedBlogsUrlParams = {
  entity_type: 'blog',
  entity_slug: '8-common-data-structures-every-programmer-must-know',
  domain: 'blog,section,course,word',
  take: 6,
};
onBeforeMount(async () => {
  try {
    relatedBlogsData.value = await fetchData(
      URL.RELATED_BLOGS,
      relatedBlogsUrlParams,
    );
    relatedBlogsExist.value = true;
  } catch (error) {
    relatedBlogsExist.value = false;
    console.error(`Failed to fetch data from url: ${error.message}`);
  }
});

provide('relatedBlogsData', relatedBlogsData);
</script>
