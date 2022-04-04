<template>
  <div class="search">
    <input
      type="text"
      name="search-input"
      id=""
      class="search-input"
      @input="handleInput"
    />
    <span class="search-icon"><search-icon /></span>
  </div>
</template>

<script>
import SearchIcon from './svgs/SearchIcon.vue';
export default {
  props: {
  onSearchInput: {
      type: Function,
      required: true,
    },
  },
  components: { SearchIcon },
  data() {
    return { searchInput: '' };
  },
  methods: {
    handleInput({target:{value}}) {
    this.onSearchInput(value)
    },
  },
};
</script>

<style scoped lang="scss">

</style>
