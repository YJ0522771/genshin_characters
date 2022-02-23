<template>
  <h1>Genshin Characters</h1>
  <div>
    <CheckBoxList
    v-for="s in selection"
    :key = s.title
    :title="s.title"
    :list="s.list"
    />
  </div>
  
</template>

<script>
import CheckBoxList from './components/CheckBoxList.vue'
import selection from '../public/selection.json'

export default {
  name: 'App',
  components: {
    CheckBoxList
  },
  data: function () {
    return {
      selection: {},
    }
  },
  created: function () {
    this.selection = selection
  },
  methods: {

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
