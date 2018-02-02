<template>
  <div id="app">
    <h1 v-html="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew()">
    <ul>
      <li v-for="item in items" v-bind:key="{finished:item.isFinished}" v-on:click="toggleFinish(item)">
        {{ item.label }}
      </li>
    </ul>
    <component-a></component-a>
  </div>
</template>

<script>
import Store from "./store.js";
import ComponentA from './components/componentA';

export default {
  data: function() {
    return {
      title: "this is todo list",
      items: Store.fetch(),
      newItem: ""
    };
  },
  components: {
    ComponentA
  },
  watch: {
    items: {
      handler: function(items) {
        Store.save(items);
      },
      deep: true
    }
  },
  methods: {
    toggleFinish: function(item) {
      item.isFinished = !item.isFinished;
    },
    addNew: function() {
      console.log(this.newItem);
      this.items.push({
        label: this.newItem,
        isFinished: false
      });
      this.newItem = "";
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.finished {
  text-decoration: underline;
}
</style>
