<script>
import Word from "./Word.vue";

export default {
  components: {Word},
  props: ['words'],
  methods: {
    onWordTapped: function (wordId) {
      this.$emit('tapped', wordId)
    }
  }
}
</script>

<template>
  <div class="tags are-medium">
    <Word class="tag is-light" v-for="word in words" :word="word" @tapped="onWordTapped"/>
  </div>
</template>

<style scoped>
</style>
