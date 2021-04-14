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
            <input type="text" class="form-control" placeholder="" v-model="nombre_pokemon" />
          </div>
          <button type="button" class="btn btn-primary mt-4" @click="getPoke">Buscar</button>
        </div>
      </div>
      <div class="row mt-5">
        <div class="col-12">
          <img :src="pokeData && pokeData.sprites && pokeData.sprites.front_default" alt="pokemon" class="mb-4" />
        </div>
        <div class="col-12">
          <h2>Movimientos</h2>
          <ul>
            <li v-for="(move, i) in pokeData.moves" :key="i">
              {{move.move.name}}
            </li>
          </ul>
        </div>
        <div class="col-12">
          <h2>Habilidades</h2>
          <ul>
            <li v-for="(ability, i) in pokeData.abilities" :key="i">
              {{ability.ability.name}}
            </li>
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
      nombre_pokemon: "pikachu",
      pokeData: ""
    };
  },
  methods: {
    async getPoke() {
      const url = "https://pokeapi.co/api/v2/pokemon/";
      try {
        const req = await axios(url + this.nombre_pokemon);
        if (!req) return;
        this.pokeData = req.data;
        console.log(req.data);
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
