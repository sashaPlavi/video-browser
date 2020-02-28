<template>
  <div class="row">
    <div class="col-md-8">
      <input @change="onInput" />
    </div>
    <div class="col-md-2"></div>
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
  width: 100%;
}
div {
  text-align: center;
  margin: 20px;

  border-radius: 4px;
}
</style>
