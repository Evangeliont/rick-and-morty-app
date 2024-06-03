<template>
  <div class="pagination">
    <button @click="$emit('change-page', page - 1)" :disabled="page <= 1">
      Previous
    </button>
    <span>Page {{ page }} of {{ totalPages }}</span>
    <button
      @click="$emit('change-page', page + 1)"
      :disabled="page >= totalPages"
    >
      Next
    </button>
  </div>
</template>

<script>
export default {
  props: {
    page: Number,
    totalPages: Number,
  },
};
</script>

<style scoped>
.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}
</style>
