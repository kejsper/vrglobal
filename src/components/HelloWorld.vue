<template>
  <header class="hello">
    <h1>{{ msg }}</h1>
  </header>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Hello VR Global!'
    }
  }
}
</script>

<style lang="scss" scoped>
.hello {
  margin-top: 40px;
}
</style>
