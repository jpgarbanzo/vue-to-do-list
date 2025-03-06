<script>
export default {
  props: {
    msg: {
      type: String,
      required: true,
    },

    contadorLikes: {
      type: Number,
      required: false,
    },

    texto: {
      type: String,
      default: '',
    },
  },

  mounted() {
    this.inicializar()
  },

  data() {
    return {
      textoLocal: '',
    }
  },

  computed: {},

  methods: {
    notificarPadre() {
      this.$emit('cambio-de-valor', this.textoLocal)
    },

    inicializar() {
      this.textoLocal = this.texto
    },
  },

  watch: {
    texto() {
      this.textoLocal = this.texto
    },
  },
}
</script>

<template>
  <div class="greetings">
    <!-- <h1 class="green">{{ msg }}</h1> -->
    <h1 class="green">Hijo</h1>
    <p>{{ contadorLikes }}</p>
    <hr />

    <input v-model="textoLocal" v-on:input="notificarPadre" />

    <p>Texto que viene desde el padre: {{ texto }}</p>
    <p>Texto local: {{ textoLocal }}</p>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
