<script>
import TextInputter from "./TextInputter.vue";
import ExerciseArea from "./ExerciseArea.vue";
export default {
  components: {ExerciseArea, TextInputter},
  data() {
    return {
      text: ""
    }
  },
  methods: {
    onTextSubmitted: function (text) {
      this.text = text
    }
  }
}
</script>

<template>
  <TextInputter @submitted="onTextSubmitted"/>
  <ExerciseArea :text="text" />
</template>

<style scoped>
</style>
