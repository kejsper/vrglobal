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
h1, h2, h3, h4 {
  font-weight: normal;
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
// vue animations
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
