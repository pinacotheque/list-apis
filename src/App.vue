<template>
  <the-header />
  <the-opening></the-opening>
  <filter-list @get-entries="getEntries"></filter-list>
  <the-table :info="info" :count="count" :selected="selected" />
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import FilterList from "./components/FilterList.vue";
import axios from "axios";
import TheTable from "./components/TheTable.vue";
import TheOpening from "./components/TheOpening.vue";

export default {
  name: "App",
  components: {
    TheHeader,
    FilterList,
    TheTable,
    TheOpening,
  },
  data() {
    return {
      selected: false,
      info: {},
      count: 0,
    };
  },
  mounted() {
    this.getEntries({});
  },
  methods: {
    async getEntries({ search = " ", category = " " }) {
      let response = await axios.get(
        "https://api.publicapis.org/entries?title=" +
          search +
          "&category=" +
          category
      );
      this.selected = true;
      this.info = response.data.entries;
      this.count = response.data.count;

      console.log(this.count);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

body {
  margin: 0;
  font-family: "Roboto", sans-serif;
  font-weight: 500;
  background-color: rgb(236, 236, 236);
  text-align: center;
}
</style>
