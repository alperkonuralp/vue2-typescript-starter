<template>
  <div class="detail">
    <table>
      <tbody>
        <tr>
          <th>#</th>
          <td>{{ item.id }}</td>
        </tr>
        <tr>
          <th>Title</th>
          <td>{{ item.title }}</td>
        </tr>
        <tr>
          <th>First Name</th>
          <td>{{ item.first_name }}</td>
        </tr>
        <tr>
          <th>Last Name</th>
          <td>{{ item.last_name }}</td>
        </tr>
        <tr>
          <th>User Name</th>
          <td>{{ item.username }}</td>
        </tr>
        <tr>
          <th>EMail</th>
          <td>{{ item.email }}</td>
        </tr>
        <tr>
          <th>Gender</th>
          <td>{{ item.gender }}</td>
        </tr>
        <tr>
          <th>Phone Number</th>
          <td>{{ item.phone_number }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { User, users } from "@/data/users";

@Component
export default class ListView extends Vue {
  private item: User | null = null;
  private id = 0;

  mounted() {
    this.id = parseInt(this.$route.params.id);
    this.item = users.find((x) => x.id === this.id) || null;
  }
}
</script>

<style lang="scss" scoped>
table {
  margin: 0 auto;
  tbody tr {
    th {
      text-align: right;
    }
    td {
      text-align: left;
    }
  }
}
</style>
