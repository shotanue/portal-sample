<template>
  <vue-draggable-resizable
    class="absolute flex justify-center items-center shadow-md"
    :class="[`bg-${color}-500`]"
    :x="top"
    :y="left"
    :w="100"
    :h="100"
  >
    <slot />
  </vue-draggable-resizable>
</template>

<script>
import VueDraggableResizable from 'vue-draggable-resizable'
export default {
  components: {
    VueDraggableResizable,
  },
  props: {
    top: {
      type: Number,
      required: true,
    },
    left: {
      type: Number,
      required: true,
    },
    color: {
      type: String,
      required: true,
    },
  },
}
</script>
