<template>
  <header>
    <nav class="container">
      <router-link to = "/">
        <img alt="WDEV" id="logo" src="https://raw.githubusercontent.com/william-costa/wdev-mock-site-resources/master/assets/images/wdev.svg" />
      </router-link>

      <img v-on:click="showMenu" alt="Abrir menu" id="menu-buttom" src="https://raw.githubusercontent.com/william-costa/wdev-mock-site-resources/master/assets/images/menu.svg" />
    </nav>

    <div v-on:click="showMenu" id="menu-overlay" v-if="menuActive"></div>

    <div id="menu-items" :class="{active:menuActive}">
      <img alt="WDEV" id="menu-logo" src="https://raw.githubusercontent.com/william-costa/wdev-mock-site-resources/master/assets/images/wdev.svg" />

      <ul>
        <li v-on:click="showMenu"><router-link to = "/">Home</router-link></li>
        <li v-on:click="showMenu"><router-link to = "/videos">Vídeos</router-link></li>
        <li v-on:click="showMenu"><router-link to = "/sobre">Sobre</router-link></li>
        <li v-on:click="showMenu"><router-link to = "/contato">Contato</router-link></li>
      </ul>
    </div>

  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      menuActive: false
    }
  },
  methods: {
    showMenu() {
      this.menuActive = !this.menuActive
    },
  }
}
</script>

<style escoped>
  header {
    background-color: var(--color-background-nav);
    height: 60px;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  nav {
    display: flex;
    justify-content: space-between;
    height: 60px;
    align-items: center;
  }

  #logo {
    width: 130px;
  }

  #menu-buttom {
    width: 30px;
  }

  #menu-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 40%;
    height: 100vh;
    background-color: #000000;
    opacity: 0.8;
  }

  #menu-logo {
    width: 110px;
    margin-top: 40px;
    margin-bottom: 10px;
  }

  #menu-items {
    position: fixed;
    top: 0;
    right: 0;
    background-color: var(--color-background-nav);
    width: 60%;
    height: 100vh;
    display: none;
    flex-direction: column;
    align-items: center;
  }

  #menu-items.active {
    display: flex;
  }

  ul {
    list-style: none;
    text-align: center;
    height: 60px;
    align-items: center;
  }

  ul li {
    margin: 20px 0;
  }

  ul li a {
    color: var(--color-text-light);
  }

  @media (min-width: 700px) {
    #menu-buttom,
    #menu-logo,
    #menu-overlay {
      display: none;
    }

    nav {
      margin-left: 10px;
    }

    #menu-items {
      display: flex;
      position: static;
      width: auto;
      height: 60px;
      margin-right: 20px;
    }

    ul {
      display: flex;
    }

    ul li {
      margin: 0;
      margin-left: 20px;
    }
  }
</style>