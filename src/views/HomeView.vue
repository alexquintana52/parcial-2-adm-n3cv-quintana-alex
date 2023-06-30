<template>
  <v-app>
    <h1 class="text-center py-10 font-weight-bold">Last Animes</h1>

    <v-container>
      <v-row class="justify-center">
        <CardAnime
          v-for="anime in animeList"
          :key="anime.mal_id"
          :anime="anime"
        />
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
// Components
import CardAnime from '../components/CardAnime.vue';

export default ({
  name: 'HomeView',
  components: {
    CardAnime,
  },
  data() {
    return {
      animeList: [],
    }
  },
  methods: {
    getData() {
      fetch(`https://api.jikan.moe/v4/seasons/now?sfw&limit=20`)
        .then(response => response.json())
        .then(data => {
          console.log(data.data)
          this.animeList = data.data
        })
    }
  },
  mounted() {
    this.getData()
  },
});

</script>

<style scoped>
</style>