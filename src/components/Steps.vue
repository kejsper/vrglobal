<template>
  <section class="steps">
    <h1>{{ msg }}</h1>
    <ul class="steps__list">
      <li v-for="(step, key) in steps"
          :key="key"
          class="steps__item">
          <button @click="setClasses(key)" class="icon" :class="{ 'icon__active': step.active, 'icon__inactive': (!step.active && !step.lastActive), 'icon__last': step.lastActive }"></button>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'Steps',
  data () {
    return {
      msg: 'This is Task 2 - Steps',
      steps: [
        {
          id: 1,
          name: 'step 1',
          active: true,
          lastActive: false
        },
        {
          id: 2,
          name: 'step 2',
          active: false,
          lastActive: false
        },
        {
          id: 3,
          name: 'step 3',
          active: false,
          lastActive: false
        }
      ]
    }
  },
  computed: {

  },
  methods: {
    setClasses (key) {
      if (this.steps[key].active || this.steps[key].lastActive) {
        this.isActive(key)
      }
    },
    isActive (key) {
      this.steps.forEach(step => {
        step.active = false
        step.lastActive = false
      })
      if (key + 2 === this.steps.length) {
        this.isLast(key)
      } else if (key + 2 > this.steps.length) {
        this.steps[0].active = true
      } else {
        this.steps[key + 1].active = true
      }
    },
    isLast (key) {
      this.steps[key + 1].lastActive = true
    }
  }
}
</script>

<style lang="scss" scoped>
.steps {
  margin-top: 200px;
  &__list {
    display: flex;
    flex-direction: row;
    align-items: center;
    list-style-type: none;
  }
  &__item {
    display: flex;
    margin: 20px 5px;
    height: 60px;
  }
}
.icon {
  display: flex;
  align-self: center;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 60px;
  background-color: #84e384;
  border-radius: 50%;
  font-size: 32px;
  color: white;
  transition: all 0.1s ease-out;
  border: none;
  &:focus {
    outline: none;
    border: none;
  }

  &__inactive {
    width: 20px;
    height: 20px;
    background-color: #DEDCE5;
    border-radius: 50%;
  }
  &__active {
    &:before {
      content: '\f105';
      font-family: FontAwesome;
    }
  }
  &__last {
    &:before {
      content: '\f00c';
      font-family: FontAwesome;
    }
  }
}
</style>
