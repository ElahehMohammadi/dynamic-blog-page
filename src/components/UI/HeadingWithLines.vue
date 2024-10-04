<template>
  <div class="heading">
    <span class="heading__line"></span>
    <h3 class="heading__title h3 fw-bolder lh-lg text-secondary-2">
      {{ title }}
    </h3>
    <span class="heading__line"></span>
  </div>
</template>

<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
});
</script>
<style lang="scss" scoped>
.heading {
  display: flex;
  flex-direction: row;
  align-content: center;
  gap: 12px;
  justify-content: center;

  &__line {
    content: '';
    display: block;
    width: 1.5rem;
    height: 0.375rem;
    border-radius: 0.25rem;
    background-color: #cac4e7;
    opacity: 1;
    align-self: center;
  }
}
</style>
