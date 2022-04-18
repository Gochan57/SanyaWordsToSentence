<script>
export default {
  data() {
    return {
      text: ""
    }
  },
  methods: {
    onTextChanged: function (e) {
      this.text = e.target.value
    },
    onSubmitButtonClicked: function () {
      this.$emit("submitted", this.text)
    }
  }
}
</script>

<template>
  <div class="section">
    <div class="block">
        Put your text here and submit
    </div>
    <div class="block">
      <textarea class="textarea wide-textarea" rows="3" @change="onTextChanged">{{text}}</textarea>
    </div>
    <div class="block">
      <button class="button is-primary" @click="onSubmitButtonClicked">Submit</button>
    </div>
  </div>
</template>

<style scoped>

.wide-textarea {
  width: 100%;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -ms-box-sizing: border-box;
  box-sizing: border-box;
}

</style>
