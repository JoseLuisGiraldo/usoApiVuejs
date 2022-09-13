<template>
  <div class="hello">
    <button @click="recargar">aleatoria</button>
    <h1>{{ msg }}</h1>
    <h2>ingresa la publicacion a realizar</h2>
    <input type="text" v-model="resultado">
    <h3>{{resultadoo}}</h3>
    <button @click="consultar">consultar</button>
    <img :src=imagen>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      imagen:'',
      resultado:'',
      resultadoo:'',

    }
  },
  props: {
    msg: String
  },
  methods: {
    recargar() {
      console.log("hola mundi")
      const URL = 'https://api.thedogapi.com/v1/images/search'
      fetch(URL).then(response => response.json()).then(data => {
        console.log(data[0])
      });
    },
    consultar() {
      
      console.log("entro a consultar")
      const URL = `http://localhost:8000/${this.resultado}`
      alert(URL)
      fetch(URL).then(response => response.json()).then(data => {
        this.resultadoo=data.respuesta
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
