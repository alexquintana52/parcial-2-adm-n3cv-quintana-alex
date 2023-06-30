<template>
  <v-app>
    <h1 class="text-center py-10 font-weight-bold">Search Anime</h1>
    <form @submit.prevent="HandleSearch">
      <input v-model="search_query" class="search-box mb-10" id="search-box" type="text" placeholder="Enter Anime Name">
    </form>
    <v-container>
      <v-row class="justify-center" v-if="animeList.length > 0">
        <CardAnime v-for="anime in animeList" :key="anime.mal_id" :anime="anime" />
      </v-row>
      <v-row v-else>
        <h3 class="text-center">Sorry, we have no results...</h3>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import CardAnime from '../components/CardAnime.vue';

export default {
  name: 'SearchView',
  components: {
    CardAnime,
  },
  data() {
    return {
      animeList: [],
      search_query: '',
    }
  },
  methods: {
    HandleSearch() {
      fetch(`https://api.jikan.moe/v4/anime?sfw&q=${this.search_query}&limit=24`)
        .then(response => response.json())
        .then(data => {
          console.log(data.data);
          this.animeList = data.data;
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