<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
    };
  },
  methods: {
    search(event) {
      this.$emit("loadCards", event.target.value);
    },
  },
};
</script>

<template>
  <select v-model="store.archetype" @change="search">
    <option
      v-for="(item, index) in store.archetypeList"
      :key="index"
      :value="item.archetype_name"
    >
      {{ item.archetype_name }}
    </option>
  </select>
</template>

<style></style>
