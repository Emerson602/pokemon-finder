<template>
  <div id="content">

  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Layout',
  data() {
    return {
      
    };
  },
  methods: {
    getPokemons() {

      let limit = 30
      let offset = 0;
      axios
        .get(`https://pokeapi.co/api/v2/pokemon?limit=${limit}&offset=${offset}`)
        .then((response) => {
          console.log(response.data); 
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
  mounted() {
    this.getPokemons();
  },
};
</script>


<style scoped>

</style>
