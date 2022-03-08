<template>
  <table class="table table-striped table-bordered" v-if="selected">
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
          <a :href="item.Link">{{ item.Link }}</a>
        </td>
      </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  props: ["info", "selected"],
};
</script>

<style scoped>
th {
  font-size: 17px;
  font-weight: 500;
  border-bottom: 1px solid grey;
  padding-bottom: 5px;
}
</style>
