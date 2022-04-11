<template>
  <div
    class="cursor-pointer"
    :style="{
      '--posX': cursorPos.x,
      '--posY': cursorPos.y,
      '--isShow': isShow ? 'inline-block' : 'none',
    }"
  >
    <b-icon-chevron-left />
    <b-icon-circle v-if="!isClick" />
    <b-icon-chevron-right />
  </div>
</template>
<script>
export default {
  data() {
    return {
      cursorPos: {
        x: 0,
        y: 0,
      },
      isShow: false,
      registerElements: [],
      isClick: false,
    }
  },
  mounted() {
    window.addEventListener('mouseover', (e) => {
      const touch = matchMedia('(hover: none)').matches
      if (touch) return
      const ele = e.target
      this.isShow = this.isDescendant(ele)
    })
    window.addEventListener('mousemove', (e) => {
      this.cursorPos = {
        x: e.clientX + 'px',
        y: e.clientY + 'px',
      }
    })
    window.addEventListener('mousedown', (e) => {
      this.isClick = true
    })
    window.addEventListener('mouseup', (e) => {
      this.isClick = false
    })
    window.addEventListener('scroll', (e) => {
      this.isShow = false
    })
  },
  methods: {
    toggleShowPointer(state) {
      this.isShow = state
    },
    isDescendant(child) {
      let node = child.parentNode
      while (node) {
        if (this.registerElements.includes(node)) {
          return true
        }
        node = node.parentNode
      }

      // Go up until the root but couldn't find the `parent`
      return false
    },
    registerHoverCursor(component) {
      this.registerElements.push(component)
    },
  },
}
</script>
<style lang="scss" scoped>
.cursor-pointer {
  cursor: pointer;
  position: fixed;
  z-index: 3;
  transform: translate(-50%, -50%);
  pointer-events: none;
  top: var(--posY);
  left: var(--posX);
  display: var(--isShow);
}
</style>
