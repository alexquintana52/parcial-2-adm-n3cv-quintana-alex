<template>
    <v-col xs="9" sm="6" md="4" lg="3">
        <v-card>
            <v-img height="400" :src="manga.images.jpg.image_url" cover>
            </v-img>
            <v-card-title>{{ manga.title }}</v-card-title>
        </v-card>
    </v-col>
</template>

<script>
export default {
    name: 'CardManga',
    props: [
        'manga'
    ],
}
</script>