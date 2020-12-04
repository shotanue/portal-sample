<template>
  <portal to="floating-objects" :order="order">
    <vue-draggable-resizable
      :key="item.id"
      class="absolute flex justify-center items-center shadow-md"
      :class="getColor(item.color)"
      :x="item.top"
      :y="item.left"
      :w="100"
      :h="100"
      @activated="$emit('onDragStart')"
    >
      <slot />
    </vue-draggable-resizable>
  </portal>
</template>

<script>
import VueDraggableResizable from 'vue-draggable-resizable'
import { Portal } from 'portal-vue'
export default {
  components: {
    VueDraggableResizable,
    Portal,
  },
  props: {
    item: {
      type: Object,
      required: true,
    },
    order: {
      type: Number,
      required: true,
    },
  },
  methods: {
    getColor(color) {
      return {
        red: 'bg-red-500',
        green: 'bg-green-500',
        blue: 'bg-blue-500',
      }[color]
    },
  },
}
</script>
