<template>
  <div class="main-content__side-bar d-lg-block d-none col-4">
    <div class="side-bar sticky-top">
      <main-content-sidebar-content-table
        :titles="titles"
      ></main-content-sidebar-content-table>
      <main-content-sidebar-action-buttons></main-content-sidebar-action-buttons>
    </div>
  </div>
</template>

<script setup>
import MainContentSidebarContentTable from '@/components/mainContent/MainContentSidebarContentTable.vue';
import MainContentSidebarActionButtons from '@/components/mainContent/MainContentSidebarActionButtons.vue';
import { inject } from 'vue';
//get the titles of the main text
const titles = inject('titles');
</script>
