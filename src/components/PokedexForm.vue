<template>
  <form class="pokemon-form" v-on:submit.prevent="search()">
    <input
      class="pokemon-input"
      type="text"
      name="pokemon"
      v-model="pokemonName"
      placeholder="Busca tu pokemon"
      autocomplete="off"
    />
    <button type="submit" class="pokemon-btn" />
  </form>
</template>

<script>
export default {
  name: "PokedexForm",

  data() {
    return {
      pokemonName: "",
      pokemonListStorage: [],
    };
  },
  mounted() {
    if (localStorage.pokemonListName) {
      this.pokemonListStorage = JSON.parse(localStorage.pokemonListName);
    }
  },
  methods: {
    search() {
      const pokemonName = this.pokemonName;
      const newPokemonId = window.isNaN(parseInt(pokemonName))
        ? pokemonName.toLowerCase()
        : pokemonName;
      console.log(newPokemonId);
      this.$emit("searchPokemon", this.pokemonName);
    },
  },
};
</script>
