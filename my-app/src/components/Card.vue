<script>
export default {
  props: {
    characterData: Object,
  },
};
</script>

<template>
  <div class="card">
    <img
      :src="characterData.card_images[0].image_url_small"
      :alt="characterData.id"
    />
    <div class="text">
      <p class="name">{{ characterData.name }}</p>
      <div>{{ characterData.archetype }}</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  width: calc(100% / 5 - 1rem);
  margin-bottom: 15px;
  background-color: darkgoldenrod;
  text-align: center;
  img {
    width: 100%;
  }
  .name {
    color: white;
    font-weight: bold;
    margin: 1rem 0;
  }
}
</style>
