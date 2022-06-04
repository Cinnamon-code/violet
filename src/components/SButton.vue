<template>
  <button @click="handleClick" type="button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "SButton",
  methods: {
    handleClick(e) {
      this.$emit('click', e)
    }
  },
  props: {
    background: {
      type: String,
      default: '#42b983'
    },
    color: {
      type: String,
      default: '#fff'
    }
  }
}
</script>

<style scoped>
button {
  border: none;
  border-radius: 4px;
  padding: 10px 0;
  background-color: #42b983;
  color: #fff;
  transition: background-color .2s;
}

button:hover {
  background-color: #63C395;
  cursor: pointer;
}
</style>
