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
    <p>{{ characterData.name }}</p>
  </div>
</template>

<style lang="scss" scoped>
.card {
  margin: 1rem;
  width: 166px;
  background-color: yellow;
}
</style>
