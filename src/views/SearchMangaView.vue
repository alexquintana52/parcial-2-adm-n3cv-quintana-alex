<template>
  <v-app>
    <h1 class="text-center py-10 font-weight-bold">Search Manga</h1>
    <form @submit.prevent="HandleSearch">
      <input v-model="search_query" class="search-box mb-10" id="search-box" type="text" placeholder="Enter Manga Name">
    </form>
    <v-container>
      <v-row class="justify-center" v-if="mangaList.length > 0">
        <CardManga v-for="manga in mangaList" :key="manga.mal_id" :manga="manga" />
      </v-row>
      <v-row class="justify-center" v-else>
        <h3>Sorry, we have no results...</h3>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import CardManga from '../components/CardManga.vue';

export default {
  name: 'SearchMangaView',
  components: {
    CardManga,
  },
  data() {
    return {
      mangaList: [],
      search_query: '',
    }
  },
  methods: {
    HandleSearch() {
      fetch(`https://api.jikan.moe/v4/manga?sfw&q=${this.search_query}&limit=24`)
        .then(response => response.json())
        .then(data => {
          console.log(data.data);
          this.mangaList = data.data;
          this.search_query = '';
        })
    }
  },
  mounted() {
    this.HandleSearch()
  },
}

</script>

<style>
.search-box {
  appearance: none;
  background: none;
  border: none;
  outline: none;

  background-color: #F3F3F3;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.15);

  display: block;
  width: 100%;
  max-width: 600px;
  padding: 15px;
  border-radius: 8px;

  color: #313131;
  font-size: 20px;

  transition: 0.4s;
  margin: 0 auto;
}
</style>