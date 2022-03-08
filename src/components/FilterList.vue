<template>
  <h3>Get Categories</h3>
  <select v-model="selected" @change="changeCategory">
    <option v-for="category in categories" :key="category" :id="category">
      {{ category }}
    </option>
  </select>
  <h3>Search By Title</h3>
  <input v-model="search" placeholder="Search" />
  <button @click="searchTitle">Search</button>
</template>

<script>
import axios from "axios";
export default {
  emits: ["get-entries"],
  data() {
    return {
      categories: [],
      selected: " ",
      search: "",
    };
  },
  async mounted() {
    let response = await axios.get("https://api.publicapis.org/categories");
    this.categories = response.data.categories;
  },
  methods: {
    changeCategory() {
      this.$emit("get-entries", {
        search: this.search,
        category: this.selected,
      });
    },
    searchTitle() {
      this.$emit("get-entries", {
        search: this.search,
        category: this.selected,
      });
    },
  },
};
</script>

<style scoped>
* {
  text-align: center;
}
.filter-option {
  min-width: 25rem;
}
select {
  width: 20rem;
  height: 3rem;
  padding-block: 5px;
  padding-inline: 5px;
  border-radius: 20px;
  border: 1px solid rgb(214, 214, 214);
  margin-block: 5px;
  margin-left: 10px;
  text-align: center;
}
input {
  padding: 10px;
  width: 15rem;
  border-radius: 20px;
  border: 1px solid rgb(214, 214, 214);
  font-size: 18px;
}
</style>
