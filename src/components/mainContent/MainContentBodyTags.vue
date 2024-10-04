<template>
  <div
    class="main-content__text--footer text-footer d-flex justify-content-between align-content-lg-between"
  >
    <div class="text-footer__tags">
      <button
        v-for="tag in tags"
        :key="tag"
        class="btn sub1 lh-base bg-gray-light border-0"
        @click.prevent
      >
        {{ tag.name }}
      </button>
    </div>
    <div class="text-footer__report">
      <button class="btn border border-secondary-2" @click.prevent>
        <img
          src="@/assets/img/icons/flag.svg"
          alt="flag icon"
          class="icon-sm"
        />
        <span class="title4 text-secondary-2 lh-base">گزارش محتوا</span>
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  tags: {
    type: Array,
    required: true,
  },
});
</script>
<style lang="scss" scoped>
.text-footer {
  gap: 20px;
  @media (max-width: 992px) {
    flex-direction: column;
    justify-content: space-between;
  }

  &__tags {
    display: flex;
    align-items: center;
    gap: 8px;
    flex-wrap: wrap;
  }

  .btn {
    border-radius: 8px;
  }

  &__report {
    align-self: flex-end;
    white-space: nowrap;
  }
}
</style>
