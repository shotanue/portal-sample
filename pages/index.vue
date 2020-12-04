<template>
  <main class="relative w-screen h-screen">
    <floatable
      v-for="(item, index) in items"
      :key="index"
      :item="item"
      :order="getOrder(item.id)"
      @onDragStart="bringToFront(item.id)"
    >
      <div>{{ item.text }}</div>
    </floatable>
    <PortalTarget name="floating-objects" multiple />
  </main>
</template>

<script>
import { PortalTarget } from 'portal-vue'
import floatable from '~/components/floatable.vue'

export default {
  components: {
    floatable,
    PortalTarget,
  },
  data() {
    return {
      items: [
        { id: 'a', top: 0, left: 0, text: 'A', color: 'green' },
        { id: 'b', top: 50, left: 50, text: 'B', color: 'red' },
        { id: 'c', top: 100, left: 100, text: 'C', color: 'blue' },
      ],
      floatingOrder: ['a', 'b', 'c'],
    }
  },
  methods: {
    bringToFront(identifier) {
      const newList = this.floatingOrder.filter((k) => k !== identifier)
      newList.push(identifier)
      this.floatingOrder = newList
    },
    getOrder(identifier) {
      const notFound = -1
      const index = this.floatingOrder.findIndex((k) => k === identifier)
      const offset = 1 // portalが受け付けるorderが1始まりなので
      return index === notFound ? this.floatingOrder.length + offset : index
    },
  },
}
</script>
