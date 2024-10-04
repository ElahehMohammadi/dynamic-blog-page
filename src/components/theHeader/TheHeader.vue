<template>
  <header class="col-12 row">
    <!-- Navbar -->
    <nav class="navbar navbar-expand-md container col-12">
      <!-- Navbar Container -->
      <div class="nav-container">
        <!-- Logo -->
        <a class="navbar-brand order-1" href="#">
          <img
            class="logo"
            alt="SokanAcademi logo"
            src="@/assets/img/icons/Logo.svg"
          />
        </a>
        <!--the Navigation bar-->
        <the-header-navbar></the-header-navbar>
        <!-- Login btn -->
        <the-header-login-btn></the-header-login-btn>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { provide } from 'vue';
import TheHeaderNavbar from '@/components/theHeader/TheHeaderNavbar.vue';
import TheHeaderLoginBtn from '@/components/theHeader/TheHeaderLoginBtn.vue';
//provide the current open page to be highlighted
const currentPage = 'weblog';
provide('currentPage', currentPage);
</script>

<style lang="scss"></style>
