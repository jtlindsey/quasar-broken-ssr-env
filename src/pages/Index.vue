<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-full.svg"
    >
    <h1 style="background-color: lightblue">What is val? {{v}}</h1>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      v: ''
    }
  },
  async mounted() {
    try {
      const v = await this.$axios.get('/api/broken-env')
      console.log('what is v', v.status, v.data)
      this.v = v.data
    } catch (error) {
      console.log('what is error', error, error.response)
    }
  }
}
</script>
