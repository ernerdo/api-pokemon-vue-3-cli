<template>
  <form class="pokemon-form" v-on:submit.prevent="search()">
    <VueMultiselect
      v-model="pokemonName"
      :closeOnSelect="true"
      :options="pokemonListStorage"
      placeholder="Search pokemon"
      @select="onSelect"
    >
    </VueMultiselect>
  </form>
</template>

<script>
import VueMultiselect from "vue-multiselect";
export default {
  name: "PokedexForm",
  components: { VueMultiselect },
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
  computed: {
    searchPokemon() {
      return this.pokemonListStorage.filter((pokemon) => {
        return pokemon.toLowerCase().includes(this.pokemonName.toLowerCase());
      });
    },
  },
  methods: {
    search() {
      if (this.pokemonName) {
        this.$emit("searchPokemon", this.pokemonName);
      }
    },
    onSelect(option) {
      if (option) {
        this.pokemonName = option;
        this.search();
      }
    },
  },
};
</script>
<style src="vue-multiselect/dist/vue-multiselect.css"></style>
