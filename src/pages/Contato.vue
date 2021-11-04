<template>
  <div class="main">
    <section class="container">
      <h1>Contato</h1>

      <section class="contacts">
        <div v-for="(contact, index) in contacts" :key="index" class="contact">
          <div class="contact-title">{{ contact.title }}</div>
          <a :href="contact.link" target="_blank">{{ contact.link }}</a>
        </div>
      </section>

    </section>
  </div>
</template>

<script>
  import api from '@/services/api'

  export default {
    name: 'Contato',
    data() {
      return {
        contacts: []
      }
    },

    mounted() {
      api.get('/contacts.json').then(response => {
        this.contacts = response.data
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

  .contacts {
    margin-bottom: 40px;
    color: var(--color-text-dark);
  }

  .contact-title {
    font-weight: 600;
    font-size: 18px;
  }

  .contact a {
    color: var(--color-text-dark);
  }

  .contact {
    margin-bottom: 20px;
  }

</style>