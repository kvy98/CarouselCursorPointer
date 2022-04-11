<template>
  <div>
    <nuxt />
    <cursor-pointer ref="cursor" />
  </div>
</template>
<script>
import CursorPointer from '../components/CursorPointer.vue'
export default {
  components: { CursorPointer },
  provide() {
    return { registerHoverOn: this.registerHoverOn }
  },
  methods: {
    registerHoverOn(component) {
      this.$refs.cursor.registerHoverCursor(component)
    },
  },
}
</script>
