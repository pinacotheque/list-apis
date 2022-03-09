<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <h3>
          <span class="name">Hello, I'm Gamze!</span> I've built this list APIs
          page and here is a quick introduction of the page.
        </h3>
        <h4>
          Page is showing all APIs available on https://api.publicapis.org/. All
          the list and its properties are shown in the table below. You can see
          all API categories in the list and filter by category. Also if you're
          looking for a spesific API you can search by title. Every page refresh
          there is a random one at the right.
          <br />
          Have a nice day!
          <br />
        </h4>
      </div>
      <hr />

      <div class="col random">
        <h2>Random Pick</h2>
        <h3>{{ random.API }}</h3>
        <h4>{{ random.Description }}</h4>
        <a :href="random.Link">Visit</a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      random: {},
    };
  },
  async mounted() {
    let response = await axios.get("https://api.publicapis.org/random");
    this.random = response.data.entries[0];
  },
};
</script>

<style scoped>
* {
  font-weight: 500;
}
.container {
  margin-inline: 12%;
}
.row {
  display: flex;
  justify-content: space-around;
}
.name {
  color: #29c95d;
}
.col {
  width: 46%;
  text-align: left;
}
.random {
  margin-left: 50px;
  width: 35%;
}
@media screen and (max-width: 900px) {
  .row {
    display: block;
  }
  .col {
    width: 90%;
  }
  .random {
    margin-left: 0;
  }
}
</style>
