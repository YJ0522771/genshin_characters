<template>
  <div>
    <span
    v-for="e of info"
    :key="e">
    {{ e }} |
    </span>
  </div>
</template>

<script>
export default {
  name: 'CheckBoxList',
  props: {
    info: Object
  },
  data: function () {
    return {
      
    }
  },
}
</script>

<style>

</style>