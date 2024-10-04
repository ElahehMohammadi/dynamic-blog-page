<template>
  <div class="side-bar__content-table">
    <div class="side-bar__content-table--heading">
      <img src="@/assets/img/icons/list.svg" alt="list icon" class="icon-xlg" />
      <span class="h6 fw-bolder lh-lg">در این مقاله می‌خوانید</span>
    </div>
    <nav
      id="side-bar"
      ref="contentTable"
      class="side-bar__content-table--content"
    >
      <nav class="nav nav-pills">
        <a
          v-for="title in titles"
          :key="title"
          class="nav-link title"
          :href="`#${title.id}`"
        >
          <img
            src="@/assets/img/icons/line.svg"
            alt="line icon"
            class="icon-md"
          />
          <span class="sub1 text-secondary-2">{{ title.name }}</span>
        </a>
      </nav>
    </nav>
  </div>
</template>

<script setup>
defineProps({
  titles: {
    type: Array,
    required: true,
  },
});
</script>
