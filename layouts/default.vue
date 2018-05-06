<template>
  <v-app light>
    <toolbar />
    <br />
    <v-flex xs12 sm6 offset-sm3>
      <v-card light>
          <center>
            <div style="width: 80%;">
              <nuxt />
            </div>
          </center>
        </v-card>
      </v-flex>
  </v-app>
</template>

<script>
import Toolbar from '@/components/Toolbar'

  export default {
    components: {
      Toolbar
    },
    data() {
      return {
      }
    }
  }
</script>