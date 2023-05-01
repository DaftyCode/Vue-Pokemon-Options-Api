<template>
  <div class="pokemon-container">
    <img :src="imgSrc" class="hidden-pokemon" alt="pokemon" />

    <img v-if="showPokemon" :src="imgSrc" class="fade-in" alt="pokemon" />
  </div>
</template>

<script>
export default {
  props: {
    pokemonId: {
      type: Number,
      default: 4,
      required: true,
      validator(value) {
        return value >= 0 && value <= 800;
      },
    },
    showPokemon: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
  computed: {
    imgSrc() {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`;
    },
  },
};
</script>

<style lang="scss" scoped>
.pokemon-container {
  height: var(--pokemon-height);
  display: flex;
  justify-content: center;
  margin-top: 2rem;

  img {
    height: var(--pokemon-height);
    position: absolute;
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
  }

  .hidden-pokemon {
    filter: brightness(0);
  }
}
</style>
