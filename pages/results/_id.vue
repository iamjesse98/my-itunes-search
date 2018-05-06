<template>
  <div>
    <div v-if="albums.length > 0">
        <h1>Results for {{ $route.params.id }}</h1>
            <!-- {{ $store.state.albums }} -->
            <!-- {{ albums }} -->
                <div class="vuebar-element" v-bar>
                <v-card>
                    <v-container
                        fluid
                        style="min-height: 0;"
                        grid-list-lg
                    >
                        
                        <v-layout row wrap>
                            <card v-for="album in albums" :key="album.collectionViewUrl" :album="album.collectionCensoredName" :url="album.collectionViewUrl" :med="album.artworkUrl100" :copy="album.copyright" :genre="album.primaryGenreName" />
                        </v-layout>
                    </v-container>
                </v-card>
                </div>
        <br />
    </div>
    <div v-else>
        <v-card>Could not find album.</v-card>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import Card from '@/components/Card'

export default {
//   middleware: 'search',
  components: {
      Card
  },
  async asyncData( { params } ) {
      const { data } = await axios.get(`https://itunes.apple.com/search?term=${params.id}&entity=album`)
      return { albums: data.results }
  }
}
</script>

<style scoped>
.vuebar-element {
  height: 500px;
  width: 100%;
  max-width: 500px;
  background: #dfe9fe;
}


.vb > .vb-dragger {
    z-index: 5;
    width: 12px;
    right: 0;
}

.vb > .vb-dragger > .vb-dragger-styler {
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-transform: rotate3d(0,0,0,0);
    transform: rotate3d(0,0,0,0);
    -webkit-transition:
        background-color 100ms ease-out,
        margin 100ms ease-out,
        height 100ms ease-out;
    transition:
        background-color 100ms ease-out,
        margin 100ms ease-out,
        height 100ms ease-out;
    background-color: rgba(48, 121, 244,.1);
    margin: 5px 5px 5px 0;
    border-radius: 20px;
    height: calc(100% - 10px);
    display: block;
}

.vb.vb-scrolling-phantom > .vb-dragger > .vb-dragger-styler {
    background-color: rgba(48, 121, 244,.3);
}

.vb > .vb-dragger:hover > .vb-dragger-styler {
    background-color: rgba(48, 121, 244,.5);
    margin: 0px;
    height: 100%;
}

.vb.vb-dragging > .vb-dragger > .vb-dragger-styler {
    background-color: rgba(48, 121, 244,.5);
    margin: 0px;
    height: 100%;
}

.vb.vb-dragging-phantom > .vb-dragger > .vb-dragger-styler {
    background-color: rgba(48, 121, 244,.5);
}
</style>
