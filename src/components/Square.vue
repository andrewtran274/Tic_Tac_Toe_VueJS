<template>
  <button class="square" @click="handleClick">
    {{ value }}
  </button>
</template>

<script>
export default {
  props: {
    value: String,
  },
  methods: {
    handleClick() {
      this.$emit("click");
    },
  },
};
</script>

<style scoped>
/* CSS styles for the square */
.square {
  width: 40px;
  height: 40px;
  font-size: 20px;
  text-align: center;
  line-height: 40px;
  background-color: #fff;
  border: 1px solid #999;
  float: left;
  margin-right: -1px;
  margin-top: -1px;
}

.square:focus {
  outline: none;
}
</style>
