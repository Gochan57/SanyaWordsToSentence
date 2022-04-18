<script>
export default {
  props: ['word'],
  methods: {
    onWordTapped: function (word) {
      this.$emit('tapped', word.id)
    }
  }
}
</script>

<template>
  <span @click="onWordTapped(word)">{{word.value}}</span>
</template>

<style scoped>
</style>
