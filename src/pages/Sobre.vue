<template>
  <div class="main">
    <section class="container">
      <h1>Sobre</h1>

      <div class="about" v-html="about"></div>

    </section>
  </div>
</template>

<script>
  import api from '@/services/api'

  export default {
    name: 'Sobre',
    data() {
      return {
        about: ''
      }
    },

    mounted() {
      api.get('/about.json').then(response => {
        this.about = response.data.about
      })
    }
  }
</script>

<style scoped>
  .main {
    width: 100%;
    min-height: calc(100vh - 120px);
    padding: 20px;
  }

  .about {
    margin-bottom: 40px;
    color: var(--color-text-dark);
    text-align: justify;
  }

</style>