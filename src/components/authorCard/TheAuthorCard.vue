<template>
  <section class="author-card__section row col-12">
    <div class="author-card__section__container container">
      <div class="author-card border-gray-light col-lg-8 col-md-10 mx-auto">
        <img
          :src="blogData.author.avatar || fallbackImage"
          :alt="String(blogData.author.full_name) + ' profile picture'"
          class="author-card__avatar"
        />

        <div class="author-card__content">
          <div class="author-card__info col-12">
            <div class="author-card__info--name">
              <span class="title3 lh-base text-secondary-2">{{
                blogData.author.full_name
              }}</span>
              <img
                v-if="authorIsVerified"
                src="@/assets/img/icons/verify.svg"
                alt="verify icon"
                class="icon-md"
              />
            </div>
            <div class="author-card__info--describe">
              <p class="sub1 lh-base text-gray-dark">
                {{ blogData.author.bio }}
              </p>
            </div>
          </div>
          <div class="author-card__button btn border border-secondary-2">
            <span class="title4 lh-base text-secondary-2">مشاهده پروفایل</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Fallback image for author(null or load failure)
import fallbackImage from '@/assets/img/blogAuthorFallback.png';
import { inject } from 'vue';

const blogData = inject('blogData');
const authorIsVerified = true;
</script>
