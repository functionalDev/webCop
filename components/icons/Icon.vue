

<template>
  <img :src="url">
</template>
<script>
import iconConfig from './IconConfigExternal';
export default {
  name: 'dynamic-icon',
  props: ['type'],
  computed: {
      url() {
          if (!this.type || !iconConfig) {
              return null
          }
          return iconConfig[this.type];
      },
  },
}
</script>
<style scoped>
</style>
