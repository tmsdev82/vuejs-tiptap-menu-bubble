<template>
  <label class="text-reader">
    Load File
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

  border: 2px solid rgb(99, 99, 165);
  color: rgb(99, 99, 165);
  border-radius: 5px;
  padding: 8px 12px;
  cursor: pointer;
}

.text-reader:hover {
  color:white;
  background-color: rgb(99, 99, 165);
}

.text-reader input {
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  opacity: 0;
}
</style>