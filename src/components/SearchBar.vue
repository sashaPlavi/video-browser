<template>
  <div>
    <input @input="onInput" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput: function(e) {
      this.$emit("termChange", e.target.value);
    }
  }
};
</script>

<style scoped>
input {
  width: 80%;
}
div {
  text-align: center;
  margin: 20px;
}
</style>
