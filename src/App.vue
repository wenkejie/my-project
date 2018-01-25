<template>
  <div id="app">
    <h1 v-html="title"></h1>
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}">
        {{item.label}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      title: 'this is todo list',
      items: [
        {
          label: 'coding',
          isFinished: false
        },
        {
          label: 'walking',
          isFinished: true
        }
      ],
      liClass: 'thisisLiClass'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.finished{
  text-decoration: underline;
}
</style>
