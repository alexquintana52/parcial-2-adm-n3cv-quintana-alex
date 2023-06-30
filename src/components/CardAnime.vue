<template>
    <v-col xs="9" sm="6" md="4" lg="3">
        <v-card>
            <v-img height="400" :src="anime.images.jpg.image_url" cover class="text-white">
            </v-img>
            <v-card-title>{{ anime.title }}</v-card-title>
        </v-card>
    </v-col>
</template>

<script>
export default {
    name: 'CardAnime',
    props: [
        'anime'
    ],
}
</script>