<template>
  <q-item
    :class="{ 'q-item-active': node.children?.length > 0 }"
    clickable
    @click="!node.children?.length && node.handler ? node.handler() : null"
    @mouseover="handleMouseOver"
    @mouseleave="handleMouseLeave"
  >
    <q-item-section>{{ node.name }}</q-item-section>
    <q-item-section v-if="node.children?.length > 0" side>
      <q-icon name="keyboard_arrow_right" />
    </q-item-section>
    <q-menu
      v-if="node.children?.length > 0"
      anchor="top end"
      self="top start"
      content-class="bg-grey-4 text-brown-7 header-nav-title"
      transition-show="scale"
      transition-hide="scale"
    >
      <q-list>
        <template v-for="child in node.children" :key="child.name">
          <RecursiveMenuItem :node="child" />
        </template>
      </q-list>
    </q-menu>
  </q-item>
</template>

<script>
export default {
  name: "RecursiveMenuItem",
  props: {
    node: {
      type: Object,
      required: true,
    },
  },
  methods: {
    handleMouseOver() {
      // Placeholder for any mouse-over logic
    },
    handleMouseLeave() {
      // Placeholder for any mouse-leave logic
    },
  },
};
</script>

<style scoped>
.q-item-active {
  background-color: var(--q-color-grey-2);
}
</style>
