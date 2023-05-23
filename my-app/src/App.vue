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
      arch: "&archetype=",
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
    changeCards(link) {
      let archLink = this.arch + link;
      if (link != null && link != "") {
        archLink = this.arch + link;
      } else {
        archLink = "";
      }
      axios
        .get(
          "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0" +
            archLink
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
    <Search @loadCards="changeCards(store.archetype)"></Search>
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
