<template>
  <div style="max-width: 1000px; margin: auto">
    <cursor-hover-wrapper>
      <CarouselFreeMode />
    </cursor-hover-wrapper>
    <div style="height: 200px"></div>
    <cursor-hover-wrapper>
      <CarouselFreeMode />
    </cursor-hover-wrapper>
  </div>
</template>
<script>
import CarouselFreeMode from '../components/CarouselFreeMode.vue'
import CursorHoverWrapper from '../components/CursorHoverWrapper.vue'
export default {
  components: { CarouselFreeMode, CursorHoverWrapper },
  layout: 'public',
}
</script>
