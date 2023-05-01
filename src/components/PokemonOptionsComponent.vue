<template>
  <div class="options-container" v-if="pokemons && pokemons.length > 0">
    <ul>
      <li
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        @click="$emit('selection', pokemon.id)"
      >
        {{ pokemon.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
    props: {
      pokemons: {
        type: Array,
        required: true,
      },
    },
  };
</script>

<style lang="scss" scoped>
.options-container {
  display: flex;
  justify-content: center;
  margin-top: 2rem;

  ul {
    list-style-type: none;

    li {
      background-color: white;
      border-radius: 5px;
      border: 1px solid var(--border-color);
      cursor: pointer;
      margin-bottom: 0.8rem;
      width: 250px;
      padding: 0.5rem;
      text-align: center;

      &:hover {
        background-color: var(--button-hover-color);
      }
    }
  }
}
</style>
