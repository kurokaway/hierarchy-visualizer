<template>
  <label class="text-reader">
    Open File
    <input type="file" @change="loadTextFromFile">
  </label>
</template>

<script>
export default {
  methods: {
    loadTextFromFile(ev) {
      const file = ev.target.files[0];
      const reader = new FileReader();

      reader.onload = e => this.$emit("load", e.target.result);
      reader.readAsText(file);
    }
  }
};
</script>

<style>
.text-reader {
  position: relative;
  overflow: hidden;
  display: inline-block;

  /* Fancy button looking */
  border-radius: 5px;
  padding: 4px 12px;
  cursor: pointer;
  background-color: #ffd152;
  color: #343233;
  font-weight: 500;
}
.text-reader input {
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  opacity: 0;
}
</style>
