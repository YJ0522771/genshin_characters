<template>
<div class="container">
  <h1>Genshin Characters</h1>
  <div class="row">
    <CheckBoxList
    v-for="s in selection"
    :key = s.title
    :title="s.title"
    :list="s.list"
    />
  </div>
</div>
  
  
</template>

<script>
import CheckBoxList from './components/CheckBoxList.vue'
import selection from '../public/selection.json'
import characters from '../public/characters.json'

export default {
  name: 'App',
  components: {
    CheckBoxList
  },
  data: function () {
    return {
      selection: {},
      characters: {},
      checked: {}
    }
  },
  created: function () {
    this.selection = selection
    this.characters = characters
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

.row {
    --bs-gutter-x: 1.5rem;
    --bs-gutter-y: 0;
    display: flex;
    flex-wrap: wrap;
    margin-top: calc(-1 * var(--bs-gutter-y));
    margin-right: calc(-.5 * var(--bs-gutter-x));
    margin-left: calc(-.5 * var(--bs-gutter-x));
}

.col {
    flex: 1 0 0%;
}
</style>
