<script>
import CardList from "./components/CardList.vue";
import axios from "axios";
import { store } from "./store";

export default {
  data() {
    return {
      store,
    };
  },
  components: {
    CardList,
  },
  created() {
    axios
      .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
      .then((response) => (this.store.characterList = response.data.data));
  },
};
</script>

<template>
  <div class="container">
    <CardList></CardList>
  </div>
</template>

<style lang="scss" scoped>
.container {
  background-color: white;
  padding: 2rem;
  width: 1040px;
  margin: auto;
}
</style>
