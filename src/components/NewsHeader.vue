<template>
  <nav class="navbar">
    <ul class="nav-items">
      <li><logo-icon /></li>
      <li><search-input :onSearchInput="onSearchInput" /></li>
    </ul>
  </nav>
  <div class="news-header">
    <h1 class="news-header-h1">Latest News</h1>
    <p class="news-header-date">February 18, 2022</p>
    <span
      :class="['sort-icon', { 'ascending-order': isDateAscendingOrder }]"
      @click="toggleSortingOrder"
    >
      <sort-icon />
    </span>
  </div>
</template>

<script>
import LogoIcon from './svgs/LogoIcon.vue';
import SearchInput from './SearchInput.vue';
import SortIcon from './svgs/SortIcon.vue';
export default {
  props: {
    onSearchInput: {
      type: Function,
      required: true,
    },
    toggleSortingOrder: {
      type: Function,
      required: true,
    },
    isDateAscendingOrder: {
      type: Boolean,
      required: true,
    },
  },
  components: { LogoIcon, SearchInput, SortIcon },
  methods: {
    handleInput(e) {
      this.$emit('input', e);
    },
  },
};
</script>
