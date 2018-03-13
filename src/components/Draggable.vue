<template>
  <section class="draggable">
    <h1>{{ msg }}</h1>
    <div class="draggable__wrap">
      <div id="movable"
          class="draggable__drag"
          @mousedown="mouseDown"
          @mouseup="mouseUp"
          @mousemove="mouseMove"
          @blur="mouseUp"
          :style="{top: top + 'px', left: left + 'px'}"></div>
      <div id="droppable" class="draggable__drop"></div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Draggable',
  data () {
    return {
      msg: 'This is Task 3 - Drag and drop',
      isMouseDown: false,
      top: 0,
      left: 0,
      mouseX: 0,
      mouseY: 0,
      elementTop: 0,
      elementLeft: 0,
      differenceY: 0,
      differenceX: 0
    }
  },
  methods: {
    mouseDown (e) {
      const element = document.getElementById('movable')
      this.isMouseDown = true
      this.mouseY = e.clientY
      this.mouseX = e.clientX
      this.elementTop = element.offsetTop
      this.elementLeft = element.offsetLeft
      this.differenceY = this.mouseY - this.elementTop
      this.differenceX = this.mouseX - this.elementLeft
    },
    mouseUp () {
      const dropped = document.getElementById('movable')
      const dropZone = document.getElementById('droppable')
      // getting sizes and positions for dragged div and drop div
      const dropZonePositionY = dropZone.offsetTop
      const dropZoneSizeY = dropZone.offsetHeight
      const dropZonePositionX = dropZone.offsetLeft
      const dropZoneSizeX = dropZone.offsetWidth
      const droppedSizeX = dropped.offsetWidth
      const droppedSizeY = dropped.offsetHeight
      // when dragged div is not in the drop div area goes back to 0,0 position
      if (droppedSizeX + this.left < dropZonePositionX) {
        this.left = 0
        this.top = 0
      } else if (droppedSizeY + this.top < dropZonePositionY) {
        this.left = 0
        this.top = 0
      } else if (this.left > dropZonePositionX + dropZoneSizeX) {
        this.left = 0
        this.top = 0
      } else if (this.top > dropZonePositionY + dropZoneSizeY) {
        this.left = 0
        this.top = 0
      } else {
        // when we hit dragging div to drop area we set position of dragged div to the center of drop area
        this.left = dropZonePositionX + ((dropZoneSizeX - droppedSizeX) / 2)
        this.top = dropZonePositionY + ((dropZoneSizeY - droppedSizeY) / 2)
      }
      this.isMouseDown = false
    },
    mouseMove (e) {
      if (!this.isMouseDown) return
      let newMouseX = e.clientX
      let newMouseY = e.clientY
      const newElmTop = newMouseY - this.differenceY
      const newElmLeft = newMouseX - this.differenceX
      this.top = newElmTop
      this.left = newElmLeft
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.draggable {
  width: 100%;
  margin-top: 200px;
  &__wrap {
    position: relative;
    width: 80%;
    margin: 50px auto 0 auto;
  }
  &__drag {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    width: 150px;
    height: 150px;
    background-color: grey;
    cursor: pointer
  }

  &__drop {
    position: absolute;
    top: 0;
    right: 0;
    width: 250px;
    height: 250px;
    background-color: #fff;
    border: 1px solid #000;
  }
}
</style>
