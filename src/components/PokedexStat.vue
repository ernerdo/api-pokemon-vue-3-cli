<template>
  <li class="pokemon-stat">
    <span class="stat-name">
      <b>{{ item.stat.name }}: </b>
    </span>
    <span>{{ item.base_stat }}</span>
  </li>
</template>

<script>
export default {
  name: "PokedexStat",
  props: {
    item: {
      type: Object,
      default: () => {},
    },
  },
};
</script>
