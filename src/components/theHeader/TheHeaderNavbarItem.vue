<template>
  <li
    class="nav-item d-flex gap-2 flex-row align-items-center"
    :class="{
      'd-block d-md-none d-flex': iconName === 'home',
      'is-open': currentPage === iconName,
    }"
  >
    <img :src="iconUrl" :alt="iconAlt" class="icon-md d-block d-md-none" />
    <p class="sub1 lh-lg">{{ itemName }}</p>
    <span
      class="open-state"
      :class="{ 'd-block d-md-inline': currentPage === iconName }"
    ></span>
  </li>
</template>

<script setup>
//////////// SECTION //imports
import { inject, computed } from 'vue';

//////////// SECTION //get the cmp props
const props = defineProps({
  itemName: {
    type: String,
    required: true,
  },
  iconName: {
    type: String,
    required: true,
  },
});

//get the current open page to highlight the current page item
const currentPage = inject('currentPage');

//////////// SECTION //computed properties
//get the icon based on the icon name for the burger navbar
const iconUrl = computed(() =>
  require(`@/assets/img/icons/${props.iconName}.svg`),
);

//set a proper alt text for icons based on the icon
const iconAlt = computed(() => `${props.iconName} icon`);
</script>

<style></style>
