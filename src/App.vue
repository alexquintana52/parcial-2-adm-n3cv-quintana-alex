<template>
  <v-app>
    <v-toolbar>
      <v-toolbar-title></v-toolbar-title>
    </v-toolbar>
    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data: () => ({
  }),
}

</script>

<style>

</style>
