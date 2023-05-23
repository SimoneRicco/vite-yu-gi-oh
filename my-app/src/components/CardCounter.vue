<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div class="count-bar">Found {{ store.characterList.length }} Cards</div>
</template>

<style lang="scss" scoped>
.count-bar {
  background-color: black;
  color: white;
  padding: 1rem;
}
</style>
