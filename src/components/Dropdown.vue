<template>
  <nav class="dropdown" ref="dropdownMenu">
      <h4 class="dropdown__title">Pick action</h4>
      <button class="dropdown__button icon__dropdown" @click="showDropdown = !showDropdown" @blur="showDropdown = false"></button>
      <transition name="fade">
        <ul class="dropdown__list" v-if="showDropdown">
          <li class="dropdown__item">
            <input type="radio" class="form__radio" id="welcome" v-model="chooseAction" value="welcome" @change="handleChange()">
            <label class="form__label" for="welcome">
              Welcome message
            </label>
          </li>
          <li class="dropdown__item">
            <input type="radio" class="form__radio" id="steps" v-model="chooseAction" value="steps" @change="handleChange()">
            <label class="form__label" for="steps">
              Steps
            </label>
          </li>
          <li class="dropdown__item">
            <input type="radio" class="form__radio" id="draggable" v-model="chooseAction" value="draggable" @change="handleChange()">
            <label class="form__label" for="draggable">
              Draggable
            </label>
          </li>
        </ul>
      </transition>
  </nav>
</template>

<script>
export default {
  name: 'Dropdown',
  props: ['action'],
  data () {
    return {
      showDropdown: false,
      chooseAction: ''
    }
  },
  methods: {
    handleChange () {
      this.$emit('switchComponents', this.chooseAction)
    }
  },
  beforeMount () {
    this.chooseAction = this.action
  }
}
</script>

<style lang="scss" scoped>
.dropdown {
  position: relative;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;

  &__title {
    margin: 0;
  }
  &__button {
    display: block;
    margin: 0 10px;
    width: 25px;
    height: 25px;
    background-color: #D6D5E1;
    border: none;
    color: #443E6B;
    border-radius: 50%;
    cursor: pointer;
    &:focus {
      border: none;
      outline: none;
    }
  }
  &__list {
    position: absolute;
    z-index: 1;
    top: calc(100% + 12px);
    left: -10px;
    min-width: 200px;
    background-color: white;
    border: 1px solid #C6C7CE;
    border-radius: 5px;
    list-style-type: none;
    padding: 0 15px;
    text-align: left;
    box-shadow: 2px 3px 20px -4px rgba(0,0,0,0.3);
    &:after, &:before {
      content: '';
      position: absolute;
      bottom: 100%;
      border: 15px solid transparent;
      width: 0;
      height: 0;
    }
    &:before {
      border-bottom-color: #fff;
      border-width: 15px;
      position: absolute;
      top: -29px;
      left: 95px;
      z-index: 2;
    }
    &:after {
      border-bottom-color: #C6C7CE;
      border-width: 15px;
      position: absolute;
      top: -31px;
      left: 95px;
      z-index: 1;
    }
  }
  &__item {
    display: list-item;
    min-width: 200px;
    padding: 20px 0;
    border-bottom: 1px solid #E9E8EE;
    &:last-of-type {
      border-bottom: none;
    }
  }

}

.icon {
  &__dropdown {
    &::before {
      content: "\f0d7";
      font-family: FontAwesome;
    }
  }
}
</style>
