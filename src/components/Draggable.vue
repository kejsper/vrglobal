<template>
  <section class="draggable">
    <h1>{{ msg }}</h1>
  </section>
</template>

<script>
export default {
  name: 'Draggable',
  data () {
    return {
      msg: 'This is Task 3 - Drag and drop'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.draggable {
  margin-top: 200px;
}
</style>
