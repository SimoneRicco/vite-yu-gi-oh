<script>
import CardList from "./components/CardList.vue";
import axios from "axios";
import CardCounter from "./components/CardCounter.vue";
import Search from "./components/Search.vue";
import { store } from "./store";

export default {
  data() {
    return {
      store,
    };
  },
  components: {
    CardList,
    CardCounter,
    Search,
  },
  created() {
    this.changeCards();
    this.createArchtypes();
  },
  methods: {
    changeCards() {
      axios
        .get(
          "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0&archetype=" +
            store.archetype
        )
        .then((response) => (this.store.characterList = response.data.data));
    },
    createArchtypes() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/archetypes.php")
        .then((response) => (this.store.archetypeList = response.data));
    },
  },
};
</script>

<template>
  <div class="big-container">
    <Search @loadCards="changeCards"></Search>
    <div class="container">
      <CardCounter></CardCounter>
      <CardList></CardList>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  background-color: white;
  padding: 2rem;
  width: 1040px;
  margin: auto;
}
.big-container {
  width: 1040px;
  margin: auto;
}
</style>
