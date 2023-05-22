<script>
import { store } from "../store";
import Card from "./Card.vue";
export default {
  data() {
    return {
      store,
    };
  },
  components: {
    Card,
  },
};
</script>

<template>
  <div class="cards-container">
    <Card
      v-for="character in store.characterList"
      :key="character.id"
      :characterData="character"
    />
  </div>
</template>

<style lang="scss" scoped>
.cards-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>
