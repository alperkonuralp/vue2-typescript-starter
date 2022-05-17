<template>
  <div id="app">
    <img alt="Vue logo" class="logo" src="./assets/logo.png" />
    <h1>Yapılacaklar Listesi</h1>
    <div>
      <input
        v-model="newToDoText"
        type="text"
        placeholder="Yeni kayıt"
        v-on:keyup.enter="add"
      />
      &nbsp;
      <button @click="add">Ekle</button>
    </div>
    <div>
      <hr width="50%" />
    </div>
    <div>
      <h3>Liste</h3>
      <div
        v-for="(item, i) of todos"
        :key="i"
        class="list-item"
        :title="
          'Oluşturma: ' +
          item.createdDate +
          '\nDeğiştirme: ' +
          item.modifiedDate
        "
      >
        {{ i + 1 }}.
        <input
          v-model="item.isComplete"
          type="checkbox"
          @click="item.modifiedDate = new Date()"
        />
        <span :class="[item.isComplete ? 'line-through' : '']">{{
          item.text
        }}</span>
        <button class="delete-button" @click="remove(i)">Sil</button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import _ from "lodash";

@Component
export default class App extends Vue {
  private todos: ToDo[] = [];

  private newToDoText = "";

  private get isNewToDoTextEmpty() {
    return _.isNil(this.newToDoText) || _.isEmpty(this.newToDoText);
  }

  private add() {
    if (this.isNewToDoTextEmpty) {
      return;
    }

    this.todos.push({
      text: this.newToDoText,
      isComplete: false,
      createdDate: new Date(),
      modifiedDate: new Date(),
    });

    this.newToDoText = "";
  }

  private remove(index: number) {
    this.todos.splice(index, 1);
  }
}

interface ToDo {
  text: string;
  isComplete: boolean;
  createdDate: Date;
  modifiedDate: Date;
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  .logo {
    width: 10%;
  }

  .line-through {
    text-decoration: line-through;
  }

  .list-item {
    font-size: 12;
    width: 300px;
    text-align: left;
    margin: 0 auto;
    height: 25px;

    .delete-button {
      display: none;
      margin: 1px 5px;
      padding: 1px 3px;
    }

    &:hover .delete-button {
      display: initial;
    }
  }
}
</style>
