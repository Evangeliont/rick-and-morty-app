<template>
  <div>
    <Filters @apply-filters="applyFilters" />
    <div class="characters-list">
      <CharacterCard
        v-for="character in characters"
        :key="character.id"
        :character="character"
      />
    </div>
    <Pagination
      :page="page"
      :totalPages="totalPages"
      @change-page="changePage"
    />
  </div>
</template>

<script>
import CharacterCard from "../components/CharacterCard.vue";
import Pagination from "../components/Pagination.vue";
import Filters from "../components/Filters.vue";
import axios from "axios";

export default {
  components: {
    CharacterCard,
    Pagination,
    Filters,
  },
  data() {
    return {
      characters: [],
      page: 1,
      totalPages: 1,
      filters: {
        name: "",
        status: "",
      },
    };
  },
  methods: {
    fetchData() {
      const { page, filters } = this;
      axios
        .get(`https://rickandmortyapi.com/api/character`, {
          params: {
            page,
            name: filters.name,
            status: filters.status,
          },
        })
        .then((response) => {
          this.characters = response.data.results;
          this.totalPages = response.data.info.pages;
        });
    },
    changePage(newPage) {
      this.page = newPage;
      this.fetchData();
    },
    applyFilters(filters) {
      this.filters = filters;
      this.page = 1;
      this.fetchData();
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>

<style scoped>
.characters-list {
  max-width: 1170px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-template-rows: repeat(auto-fill, 250px);
  grid-auto-rows: 250px;
  grid-auto-columns: 1fr;
  grid-auto-flow: dense;
  grid-gap: 30px;
}
</style>
