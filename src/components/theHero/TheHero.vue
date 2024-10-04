<template>
  <section class="blog-hero col-12 row">
    <div class="container blog-hero__container">
      <img
        :src="blogData.cover || coverFallbackImage"
        class="blog-hero__img col-lg-4"
        alt="blog cover"
      />
      <div class="blog-hero__text-content">
        <div class="blog-hero__title">
          <h2 class="h2 lh-lg d-lg-block d-none">{{ blogData.title }}</h2>
          <h3 class="h3 lh-lg d-block d-lg-none fw-bolder">
            {{ blogData.title }}
          </h3>
        </div>
        <div class="blog-hero__data">
          <div class="blog-hero__info">
            <the-hero-data
              v-for="item in info"
              :key="item"
              :data-name="item.name"
              :data-title="item.data"
            ></the-hero-data>
          </div>
          <div class="blog-hero__author">
            <div class="blog-metadata blog-metadata--author">
              <img
                :src="blogData.author.avatar || authorFallbackImage"
                alt="author image"
                class="blog-metadata__icon icon-lg border border-gray-light"
              />
              <div class="blog-metadata__title">
                <span class="lh-lg text-secondary-2 title3">{{
                  blogData.author.full_name
                }}</span>
              </div>
            </div>
            <img
              v-if="authorIsVerified"
              src="@/assets/img/icons/verify.svg"
              alt="verify icon"
              class="icon-md"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { computed, inject } from 'vue';
import TheHeroData from '@/components/theHero/TheHeroData.vue';
// Fallback image for author(null or load failure)
import coverFallbackImage from '@/assets/img/blogCoverFallBack.png';
// Fallback image for author(null or load failure)
import authorFallbackImage from '@/assets/img/blogAuthorFallback.png';

const blogData = inject('blogData');
//filter the info to be shown
const info = computed(() => {
  return [
    {
      name: 'group',
      data: String(blogData.value.category.name),
    },
    {
      name: 'date',
      data: blogData.value.created_at,
    },
    {
      name: 'time',
      data: String(blogData.value.article.duration),
    },
    {
      name: 'rating',
      data: '156', //optional
    },
  ];
});
//temporary set the author as verified
const authorIsVerified = true;
</script>
