<template>
  <h5 class="resultNumber">{{ count }} results showing</h5>
  <div style="overflow: auto">
    <table v-if="selected">
      <thead>
        <tr>
          <th>API</th>
          <th>Auth</th>
          <th>Category</th>
          <th>Cors</th>
          <th>Description</th>
          <th>HTTPS</th>
          <th>Link</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in info" :key="index">
          <td>{{ item.API }}</td>
          <td>{{ item.Auth }}</td>
          <td>{{ item.Category }}</td>
          <td>{{ item.Cors }}</td>
          <td>{{ item.Description }}</td>
          <td>{{ item.HTTPS }}</td>
          <td>
            <a :href="item.Link">Visit</a>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  props: ["info", "selected", "count"],
};
</script>

<style scoped>
* {
  text-align: center;
  justify-content: center;
  margin: auto;
}
.resultNumber {
  font-size: 16px;
  font-weight: 500;
  color: rgb(54, 54, 54);
  text-align: left;
  width: 80%;
  padding-bottom: 10px;
}
th {
  font-size: 17px;
  font-weight: 500;
  border-bottom: 1px solid grey;
  padding-bottom: 5px;
}
table {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 80%;
  text-align: center;
}

table td,
table th {
  border: 1px solid #ddd;
  padding: 8px;
}

table tr:nth-child(even) {
  background-color: #f2f2f2;
}

table tr:hover {
  background-color: #ddd;
}

table th {
  padding-top: 12px;
  padding-bottom: 12px;
  background-color: #29c95d;
  color: white;
}
@media screen and (max-width: 900px) {
  table {
    width: fit-content;
    overflow-x: auto;
  }
}
</style>
