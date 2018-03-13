<template>
  <div id="app">
    <hello-world/>
    <dropdown :action="action" @switchComponents="handleChange"/>
    <welcome-message v-if="action === 'welcome'"/>
    <steps v-if="action === 'steps'"/>
    <draggable v-if="action === 'draggable'"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Dropdown from './components/Dropdown'
import WelcomeMessage from './components/WelcomeMessage'
import Steps from './components/Steps'
import Draggable from './components/Draggable'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Dropdown,
    WelcomeMessage,
    Steps,
    Draggable
  },
  data () {
    return {
      action: 'welcome'
    }
  },
  methods: {
    handleChange (changedAction) {
      this.action = changedAction
    }
  }
}
</script>

<style lang="scss">
@import './assets/main.scss';
</style>
