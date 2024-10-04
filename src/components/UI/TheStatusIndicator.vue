<template>
  <div class="d-flex justify-content-center vertical-spacing">
    <p v-if="isLoadFailed" class="w-100 text-center text-danger">
      <strong>خطا در ارتباط با سرور!</strong> لطفا اتصال اینترنت خود را چک کنید
    </p>
    <div v-if="isLoading" class="wait-spinner">
      <div class="spinner-border" role="status">
        <span class="visually-hidden">لطفا منتظر بمانید...</span>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  isLoadFailed: {
    type: Boolean,
    default: false,
  },
  isLoading: {
    type: Boolean,
    default: false,
  },
});
</script>
