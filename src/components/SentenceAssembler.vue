<script>
export default {
  props: ['words'],
  methods: {
    onWordTapped: function (word) {
      this.$emit('tapped', word.id)
    }
  }
}
</script>

<template>
  <div>
    <div class="box tags are-medium">
      <span class="tag is-info"> > </span>
      <span class="tag is-light" v-for="word in words" @click="onWordTapped(word)">{{word.value}}</span>
    </div>
  </div>
</template>

<style scoped>
</style>
