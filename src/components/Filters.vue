<template>
  <div class="filters">
    <input v-model="name" type="text" placeholder="Name" />
    <select v-model="status">
      <option value="">All</option>
      <option value="alive">Alive</option>
      <option value="dead">Dead</option>
      <option value="unknown">Unknown</option>
    </select>
    <button @click="applyFilters">Apply</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      status: "",
    };
  },
  methods: {
    applyFilters() {
      this.$emit("apply-filters", { name: this.name, status: this.status });
    },
  },
};
</script>

<style scoped>
.filters {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}
</style>
