<template>
  <div class="list">
    <table>
      <thead>
        <tr>
          <th></th>
          <th>#</th>
          <th>Title</th>
          <th>First Name</th>
          <th>Last Name</th>
          <th>User Name</th>
          <th>EMail</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item of users" :key="item.id">
          <td><router-link :to="'/detail/' + item.id">Detay</router-link></td>
          <td>{{ item.id }}</td>
          <td>{{ item.title }}</td>
          <td>{{ item.first_name }}</td>
          <td>{{ item.last_name }}</td>
          <td>{{ item.username }}</td>
          <td>{{ item.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { users } from "@/data/users";

@Component
export default class ListView extends Vue {
  private users = users;
}
</script>
