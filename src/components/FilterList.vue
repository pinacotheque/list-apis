<template>
  <div class="row">
    <div class="col">
      <h3>Get Categories</h3>
      <select v-model="selected" @change="changeCategory">
        <option v-for="category in categories" :key="category" :id="category">
          {{ category }}
        </option>
      </select>
    </div>
    <div class="col">
      <h3>Search By Title</h3>
      <input v-model="search" placeholder="Search" />
    </div>
  </div>
  <div class="buttons">
    <button @click="searchTitle">Search</button>
    <button @click="handleReset">Reset</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  emits: ["get-entries"],
  data() {
    return {
      categories: [],
      selected: "",
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
    handleReset() {
      this.selected = "";
      this.search = "";
      this.searchTitle();
    },
  },
};
</script>

<style scoped>
* {
  text-align: center;
  font-weight: 500;
}
.row {
  margin-inline: 20%;
  margin-top: 50px;
  display: flex;
  justify-content: space-evenly;
}
.buttons {
  margin-block: 25px;
}
.filter-option {
  min-width: 25rem;
}
select {
  width: 20rem;
  height: 3rem;
  padding-block: 10px;
  padding-inline: 15px;
  border-radius: 20px;
  border: 1px solid rgb(214, 214, 214);
  margin-left: 10px;
  text-align: center;
}
input {
  height: 3rem;
  width: 15rem;
  border-radius: 20px;
  border: 1px solid rgb(214, 214, 214);
  font-size: 18px;
}
button {
  font-size: 17px;
  padding: 15px 25px;
  margin-left: 20px;
  align-self: center;
  border-radius: 10px;
  border: 1px solid rgb(214, 214, 214);
  cursor: pointer;
}
</style>
