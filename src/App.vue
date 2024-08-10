<template>
  <div class='container pt-1'>
    <div class='card'>
      <h2>Актуальные новости {{ now }}</h2>
      <span>Открыто: <strong>{{ openRate }}</strong> | Прочитано: <strong>{{ readRate }}</strong></span>
    </div>

    <app-news v-for="item in news" :title="item.title" :key="item.id" :id="item.id" :is-open="item.isOpen"
      :was-read="item.wasRead" @open-news="openNews" @read-news="readNews" @unmark="unreadNews"></app-news>
  </div>
</template>

<script>
import AppNews from './AppNews.vue';

export default {
  name: 'App',

  data() {
    return {
      now: new Date().toLocaleDateString(),
      openRate: 0,
      readRate: 0,
      news: [
        {
          title: 'Джо Байден победил на выборах в США',
          id: 1,
          isOpen: false,
          wasRead: false
        },
        {
          title: 'Vue 3 успешно работает!',
          id: 2,
          isOpen: false,
          wasRead: false
        }
      ]
    }
  },
  components: {
    // 'app-news': AppNews
    AppNews
  },
  methods: {
    openNews(data) {
      this.openRate++
    },
    readNews(id) {
      const idx = this.news.findIndex(news => news.id === id)
      this.news[idx].wasRead = true
      this.readRate++
    },
    unreadNews(id) {
      const news = this.news.find(news => news.id === id)
      news.wasRead = false
      this.readRate--
    }
  },
  computed: {}
}
</script>

<style lang="scss"></style>
