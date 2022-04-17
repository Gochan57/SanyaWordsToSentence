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
  <div class="container">
    <div class="sentence-container">
      <span class="word-in-sentence" v-for="word in words" @click="onWordTapped(word)">{{word.value}}</span>
    </div>
  </div>
</template>

<style scoped>
.sentence-container {
  height: 40px;
  border: 1px solid gray;
  margin-top: 5px;
  margin-bottom: 5px;
  padding: 5px;
}

.word-in-sentence {
  border: 1px solid green;
  margin-right: 5px;
  padding: 2px;
}

</style>
