<template>
  <!-- menu icon for small screens -->
  <button
    class="btn navbar-toggler order-0"
    type="button"
    data-bs-toggle="offcanvas"
    data-bs-target="#offcanvasDarkNavbar"
    aria-controls="offcanvasDarkNavbar"
    aria-expanded="false"
    aria-label="Toggle navigation"
  >
    <img
      src="../../assets/img/icons/menu-1.svg"
      alt="menu icon"
      class="secondary-2 icon-md"
    />
  </button>
  <!-- theHeader content (collapsible on smaller screens) -->
  <div
    id="offcanvasDarkNavbar"
    class="offcanvas offcanvas-end flex-grow-0 flex-shrink-0 order-2"
    data-bs-scroll="true"
    tabindex="-1"
    aria-labelledby="offcanvasDarkNavbarLabel"
  >
    <div class="offcanvas-header justify-content-end">
      <button
        type="button"
        class="btn"
        data-bs-dismiss="offcanvas"
        aria-label="Close"
      >
        <img
          src="../../assets/img/icons/close-light.svg"
          alt="close sign"
          class="icon-md"
        />
      </button>
    </div>
    <!-- nav bars content container -->
    <div
      class="offcanvas-body container d-flex flex-row justify-content-between align-items-start"
    >
      <!-- Navbar items -->
      <ul class="navbar-nav w-100">
        <the-header-navbar-item
          v-for="item in navbarItems"
          :key="item"
          :item-name="item.name"
          :icon-name="item.iconName"
        ></the-header-navbar-item>
      </ul>
    </div>
  </div>
</template>

<script setup>
import TheHeaderNavbarItem from '@/components/theHeader/TheHeaderNavbarItem.vue';
// define the items in navigation bar
const navbarItems = [
  {
    name: 'خانه',
    iconName: 'home',
  },
  {
    name: 'دوره‌های آموزشی',
    iconName: 'academy',
  },
  {
    name: 'وبلاگ',
    iconName: 'weblog',
  },
  {
    name: 'مجموعه‌ها',
    iconName: 'collection',
  },
  {
    name: 'رادیوفول‌استک',
    iconName: 'podcast',
  },
  {
    name: 'فن‌واژه',
    iconName: 'glossary',
  },
];
</script>
