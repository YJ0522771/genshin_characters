<template>
  <div class="col">
    <div>
      <h2>{{ title }}</h2>
      <div
      v-for="e in list"
      :key="e">
        <input type="checkbox"
        :id="e"
        :value="e"
        v-model="checked">
        <label :for="e">{{ e }}</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CheckBoxList',
  props: {
    title: String,
    list: Array
  },
  data: function () {
    return {
      checked: []
    }
  },
}
</script>

<style>
.check-box {
  margin: auto;
}
</style>