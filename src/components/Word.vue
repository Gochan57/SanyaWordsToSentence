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
  <span class="word" @click="onWordTapped(word)">{{word.value}}</span>
</template>

<style scoped>
.word {
  border: 1px solid black;
  padding: 4px;
}
</style>
