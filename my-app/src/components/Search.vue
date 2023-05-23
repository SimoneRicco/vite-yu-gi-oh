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
  <select name="" id="">
    <option
      v-for="(item, index) in store.archetypeList"
      :key="index"
      :value="item.data.archetype_name"
    >
      {{ item.data.archetype_name }}
    </option>
  </select>
</template>

<style></style>
