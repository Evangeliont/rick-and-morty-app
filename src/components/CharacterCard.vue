<template>
  <div class="character-card">
    <h3>{{ character.name }}</h3>
    <p>Status: {{ character.status }}</p>
    <p>Species: {{ character.species }}</p>
  </div>
</template>

<script>
export default {
  props: {
    character: Object,
  },
};
</script>

<style scoped>
.character-card {
  border: 1px solid #ccc;
  width: 300px;
  padding: 10px;
  margin: 10px;
}
</style>
