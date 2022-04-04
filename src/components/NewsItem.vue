<template>
  <div class="news-item">
    <div class="news-img">
      <img :src="`${item.imgUrl}`" alt="" />
    </div>
    <div class="news-title">{{ item.title }}</div>
    <div class="news-meta">
      <span class="date">{{ newsDateFormatted }}</span>
      <span class="author">{{ item.meta.author }}</span>
    </div>
    <div class="news-description">
      <p>
        {{ item.description }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NewsItem',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  computed: {
    newsDateFormatted() {
      return this.item.meta.date.replaceAll('/', '.');
    },
  },
};
</script>
