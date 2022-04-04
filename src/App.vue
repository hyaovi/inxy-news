<template>
  <div class="layout">
    <div class="container">
      <TheNewsHeader
        :onSearchInput="onSearchInput"
        :toggleSortingOrder="toggleSortingOrder"
        :isDateAscendingOrder="isDateAscendingOrder"
      />
      <TheNews :newsList="computedNewsList" />
    </div>
  </div>
  <TheFooter />
</template>

<script>
import TheNews from './components/TheNews.vue';
import TheNewsHeader from './components/NewsHeader.vue';
import TheFooter from './components/common/TheFooter.vue';

export default {
  name: 'App',
  components: {
    TheNews,
    TheNewsHeader,
    TheFooter,
  },
  data() {
    const template = {
      title: 'News Title Ipsum Dolor Sit Amet',
      imgUrl: '/medias/news-1.png',
      meta: {
        date: '03/12/2021',
        author: 'CNN Indonesia',
      },
      description:
        'Nisi, sagittis aliquet sit rutrum. Nunc, id vestibulum quam ornare adipiscing. Pellentesque sed turpis nunc gravida pharetra, sit nec vivamus pharetra. Velit, dui, egestas nisi, elementum mattis mauris, magnis. Massa tortor nibh nulla condimentum imperdiet scelerisque... read more',
    };
    const newsList = [];
    for (let index = 0; index < 8; index++) {
      const ii = index + 1;
      const news = {
        ...template,
        title: template.title + ` ${ii}`,
        imgUrl: `/medias/news-${ii}.png`,
        meta: {
          date: `0${ii}/12/2021`,
          author: 'CNN Indonesia',
        },
      };
      newsList.push(news);
    }
    const isDateAscendingOrder = true;
    return { newsList, searchInput: '', isDateAscendingOrder };
  },
  methods: {
    onSearchInput(value) {
      this.searchInput = value;
    },
    toggleSortingOrder() {
      // toggle
      this.isDateAscendingOrder = !this.isDateAscendingOrder;
    },
  },
  computed: {
    computedNewsList() {
      return this.newsList
        .filter((news) =>
          news.title.toLowerCase().includes(this.searchInput.toLowerCase()),
        )
        .sort((a, b) => {
          if (this.isDateAscendingOrder) {
            return Date.parse(a.meta.date) > Date.parse(b.meta.date) ? -1 : 1;
          } else {
            return Date.parse(a.meta.date) > Date.parse(b.meta.date) ? 1 : -1;
          }
        });
    },
  },
};
</script>

<style lang="scss">
@import './assets/scss/app.scss';
</style>
