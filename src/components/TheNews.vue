<template>
  <div class="news-wrapper">
    <news-item v-for="(item, index) in newsList" :key="index" :item="item" />
  </div>
</template>

<script>
import NewsItem from './NewsItem.vue';
export default {
  components: { NewsItem },
  props: {
    newsList: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style></style>
