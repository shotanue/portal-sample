<template>
  <main class="relative w-screen h-screen">
    <floatable
      v-for="(item, index) in items"
      :key="index"
      :top="item.top"
      :left="item.left"
      :color="item.color"
    >
      <div>{{ item.text }}</div>
    </floatable>
  </main>
</template>

<script>
import floatable from '~/components/floatable.vue'
export default {
  components: {
    floatable,
  },
  data() {
    return {
      items: [
        { top: 0, left: 0, text: 'A', color: 'green' },
        { top: 50, left: 50, text: 'B', color: 'red' },
        { top: 100, left: 100, text: 'C', color: 'blue' },
      ],
    }
  },
}
</script>
