<template>
  <div class="side-bar__action-btn">
    <button
      class="side-bar__action-btn--comment btn border-0"
      aria-label="Go to comments section"
      @click.prevent="goToCommentsSection"
    >
      <img
        src="@/assets/img/icons/comment.svg"
        alt="comment icon"
        class="icon-md"
      />
      <span class="title3 lh-lg">دیدگاه شما</span>
    </button>
    <div class="side-bar__action-btn--save-btn">
      <button class="btn border-0" @click.prevent>
        <img
          src="@/assets/img/icons/bookmark.svg"
          alt="bookmark icon"
          class="icon-lg"
        />
      </button>
      <button class="btn border-0" @click.prevent>
        <img
          src="@/assets/img/icons/link.svg"
          alt="link icon"
          class="icon-lg"
        />
      </button>
      <button class="btn border-0" @click.prevent>
        <img
          src="@/assets/img/icons/share.svg"
          alt="share icon"
          class="icon-lg"
        />
      </button>
    </div>
  </div>
</template>

<script setup>
function goToCommentsSection() {
  document
    .getElementById('commentsSection')
    .scrollIntoView({ behavior: 'smooth' });
}
</script>
