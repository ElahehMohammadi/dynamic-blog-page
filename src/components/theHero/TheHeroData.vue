<template>
  <div class="blog-metadata" :class="`blog-metadata--${dataName}`">
    <img
      :src="icons[dataName]"
      :alt="`${dataName} icon`"
      class="blog-metadata__icon icon-lg"
    />
    <div class="blog-metadata__title">
      <span class="lh-lg text-secondary-2">{{ dataTitleComputed }}</span>
    </div>
  </div>
</template>

<script setup>
//////////// SECTION //get the props
const props = defineProps({
  dataName: {
    type: String,
    required: true,
  },
  dataTitle: {
    type: String,
    required: true,
  },
});

//////////// SECTION //constant
//the info icons
const icons = {
  group: require('@/assets/img/icons/Group.svg'),
  date: require('@/assets/img/icons/calendar.svg'),
  time: require('@/assets/img/icons/clock.svg'),
  rating: require('@/assets/img/icons/star-circle.svg'),
};

//////////// SECTION //computed properties
import { computed } from 'vue';

// Calculate time difference
function getTimeDifference(date) {
  const now = new Date();
  const pastDate = new Date(date);

  const diffYears = now.getFullYear() - pastDate.getFullYear();
  const diffMonths = now.getMonth() - pastDate.getMonth();
  const diffDays = now.getDate() - pastDate.getDate();

  if (diffYears > 0) return `${diffYears} سال پیش`;
  if (diffMonths > 0) return `${diffMonths} ماه پیش`;
  if (diffDays > 0) return `${diffDays} روز پیش`;
  return 'چند لحظه پیش';
}

// Computed property for data title
const dataTitleComputed = computed(() => {
  if (props.dataName === 'time') return props.dataTitle + ' دقیقه';
  else if (props.dataName === 'rating') return props.dataTitle + ' امتیاز';
  else if (props.dataName === 'date') {
    return getTimeDifference(props.dataTitle);
  } else {
    return props.dataTitle;
  }
});
</script>
