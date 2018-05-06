<template>
    <v-text-field
      v-model="search"
      append-icon="search"
      placeholder="Enter Artist Name"
      autofocus
      @keyup.enter="submit"
    ></v-text-field>
</template>

<script>

export default {
  components: {
  },
  data() {
    return {
      search: ''
    }
  },
  methods: {
    submit() {
      // console.log(this.search)
      this.$router.push(`results/${this.search}`)
    }
  }
}
</script>
