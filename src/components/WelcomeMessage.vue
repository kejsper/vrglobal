<template>
  <section class="welcome">
    <h3 class="welcome__title">{{ title }}</h3>
    <p class="welcome__message">{{ message }}</p>
  </section>
</template>

<script>
export default {
  name: 'WelcomeMessage',
  data () {
    return {
      title: 'My name is Kacper Tylenda.',
      message: 'I would like to join your team.'
    }
  }
}
</script>

<style lang="scss" scoped>
.welcome {
  margin-top: 150px;
}
</style>
