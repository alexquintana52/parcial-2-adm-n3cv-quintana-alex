<template>
  <v-app>
    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-app-bar-title>Anime.io</v-app-bar-title>
    </v-app-bar>
    <v-navigation-drawer app v-model="drawer" temporary>
      <v-layout class="d-flex flex-column align-center">
        <router-link class="navLink mt-10 mb-5" to="/">Home</router-link>
        <router-link class="navLink mb-5" to="/search">Search Anime</router-link>
        <router-link class="navLink" to="/searchManga">Search Manga</router-link>
      </v-layout>
    </v-navigation-drawer>
    <v-container class="mt-12">
      <router-view></router-view>
    </v-container>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data: () => ({
    drawer: true,
  }),
}

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lexend+Deca:wght@100;200;300;400;500;600;700;800&display=swap');

* {
  font-family: 'Lexend Deca', sans-serif;
}

.navLink {
  text-decoration: none;
  color: #2b2b2b;
  transition: 0.3s;
  font-weight: 500;
}

.navLink:hover {
  color: crimson;
}

</style>
