<template>
  <div id="content">
    <ul>
      <li v-for="pokemon in pokemons.results" :key="pokemon.name">
        {{ pokemon.name }} 
        <img :src="getPokemonImage(pokemon)" :alt="pokemon.name">       
      </li>
    </ul> 
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Layout',
  data() {
    return {      
      pokemons: [],
    };
  },
  methods: {
    getPokemons() {
      let limit = 150;
      axios
        .get(`https://pokeapi.co/api/v2/pokemon?limit=${limit}`)
        .then((response) => {
          this.pokemons = response.data;
        })
        .catch((error) => {
          console.error(error);
        });
    },
    
    getPokemonImage(pokemon) {
      const id = this.get_id(pokemon);
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/back/${id}.png`;
    },

    get_id(pokemon) {
      const urlParts = pokemon.url.split('/');
      return urlParts[urlParts.length - 2];
    }
  },
  mounted() {
    this.getPokemons();     
  },
};
</script>

<style scoped>
</style>
