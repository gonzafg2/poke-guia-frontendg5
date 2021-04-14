<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-12 my-5 text-center">
          <img
            src="https://raw.githubusercontent.com/PokeAPI/media/master/logo/pokeapi_256.png"
            alt="logo_pokemon"
          />
        </div>
        <div class="col-12">
          <h1>PokeGuía</h1>
        </div>
        <div class="col-12">
          <div class="form-group">
            <label class="form-label">Nombre:</label>
            <input type="text" class="form-control" placeholder="" />
          </div>
          <button type="button" class="btn btn-primary mt-4">Buscar</button>
        </div>
      </div>
      <div class="row mt-5">
        <div class="col-12">
          <img src="" alt="pokemon" class="mb-4" />
        </div>
        <div class="col-12">
          <h2>Movimientos</h2>
          <ul>
            <li></li>
          </ul>
        </div>
        <div class="col-12">
          <h2>Habilidades</h2>
          <ul>
            <li></li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      pokeAll: [],
    };
  },
  methods: {
    async getPoke() {
      const url = "https://pokeapi.co/api/v2/pokemon?offset=0&limit=1118";
      try {
        const req = await axios(url);
        if (!req) return;
        this.pokeAll = req.data.results;
        console.log(req.data.results);
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.getPoke();
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  text-align: center;
}
ul > li {
  list-style: none;
}
</style>
