<template>
  <div class="card col-12 col-sm-8">
    <img
      :src="
        String(blogData.cover_path ? blogData.cover_path : blogCoverFallbackImg)
      "
      :alt="String(blogData.title)"
      class="card-img-top"
    />
    <div class="card-body">
      <div class="card-text col-12">
        <p class="card-title lh-lg title2">{{ String(blogData.title) }}</p>
        <div class="card-text--avatar">
          <img
            :src="
              blogData.author.avatar
                ? blogData.author.avatar
                : blogAuthorFallbackImg
            "
            :alt="`${String(blogData.author.full_name)} profile picture`"
            class="icon-md"
          />
          <div class="title4 lh-base">
            {{ String(blogData.author.full_name) }}
          </div>
        </div>
      </div>
      <div class="card-body--metadata">
        <div class="card-info">
          <div class="card-info__group">
            <img
              src="@/assets/img/icons/Group.svg"
              alt="Group icon"
              class="icon-md"
            />
            <div class="sub1 lh-lg">
              {{ String(blogData.category_name) }}
            </div>
          </div>
          <!--no time for related articles in api-->
        </div>
        <img
          src="@/assets/img/icons/bookmark.svg"
          alt="Bookmark"
          class="align-self-end icon-lg"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
//////////// SECTION imports
import blogCoverFallbackImg from '@/assets/img/blogCoverFallBack.png';
import blogAuthorFallbackImg from '@/assets/img/blogAuthorFallback.png';

//////////// SECTION //the props
defineProps({
  blogData: {
    type: Object,
    required: true,
  },
});
</script>
