<script>
import Hijo from './components/Hijo.vue'

export default {
  data() {
    return {
      message: 'Mensaje desde data',
      contadorLikes: 10,
      textoPadre: 'Texto desde el padre',
    }
  },

  methods: {
    incrementarLikes() {
      this.contadorLikes = this.contadorLikes + 1
    },

    actualizarTextoPadre(texto) {
      this.textoPadre = texto
    },
  },

  components: {
    'hello-world': Hijo,
  },
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div>
      <!-- <div>
        <button v-on:click="incrementarLikes">Dar Like</button>
      </div> -->
      <h1 class="green">Padre</h1>
      <div>
        <p>Input en el padre</p>
        <input v-model="textoPadre" />
      </div>

      <hello-world
        style="margin-top: 50px"
        v-bind:msg="message"
        v-bind:contador-likes="contadorLikes"
        v-bind:texto="textoPadre"
        v-on:cambio-de-valor="actualizarTextoPadre"
      />
    </div>

    <!-- <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <a href="/about">About con tag de a</a>
      </nav>
    </div> -->
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
