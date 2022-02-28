<template>
  <div class="container">
    <h1>원신 캐릭터 분류기</h1>
    <div class="row">
      <CheckBoxList
      v-for="s in selection"
      :key = s.title
      :title="s.title"
      :list="s.list"
      @changed="updateChecked"
      />
    </div>

    <br>
    <hr>
    <br>

    <Character
    v-for="c in showList"
    :key="c"
    :info="c"
    />

  </div>
</template>

<script>
import CheckBoxList from './components/CheckBoxList.vue'
import Character from './components/Character.vue'
import selection from '../public/selection.json'
import characters from '../public/characters.json'

export default {
  name: 'App',
  components: {
    CheckBoxList,
    Character
  },
  data: function () {
    return {
      selection: {},
      characters: [],
      checked: {},
      showList: []
    }
  },
  created: function () {
    this.selection = selection
    this.characters = characters
    for (let s of this.selection) {
      this.checked[s.title] = []
    }
    this.showList = characters
  },
  methods: {
    updateChecked: function(data) {
      this.checked[data.title] = data.list
      this.updateCharacters()
    },
    updateCharacters: function() {
      this.showList = this.characters
      for (let s in this.checked) {
        if (this.checked[s].length > 0) {
          this.showList = this.showList.filter(
            chara => this.checked[s].includes(chara[s]) 
          )
        }
      }
    }
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
