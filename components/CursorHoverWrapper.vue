<template>
  <div ref="ref">
    <slot></slot>
  </div>
</template>
<script>
export default {
  inject: ['registerHoverOn'],
  mounted() {
    this.registerHoverOn(this.$refs.ref)
  },
}
</script>
