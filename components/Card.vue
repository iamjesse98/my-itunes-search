<template>
  <v-flex xs12>
    <v-card color="grey darken-2" class="white--text">
        <v-container fluid grid-list-lg>
        <v-layout row>
            <v-flex xs7 style="text-align: left;">
                <div style="font-size: 15px;">{{ album }}</div>
                <div style="font-size: 11px;">{{ genre }}</div>
                <div style="font-size: 10px;">{{ copy }}</div>
                <v-btn flat dark target="_blank" :href="url">Listen now</v-btn>
            </v-flex>
            <v-flex xs5>
            <v-card-media
                :src="med"
                height="125px"
                contain
            ></v-card-media>
            </v-flex>
        </v-layout>
        </v-container>
    </v-card>
   </v-flex>
</template>

<script>
export default {
  props: [ 'album', 'genre', 'copy', 'med', 'url' ]
}
</script>
