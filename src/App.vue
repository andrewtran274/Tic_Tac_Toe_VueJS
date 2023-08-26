<template>
  <div id="app">
    <h1>Tic-Tac-Toe</h1>
    <Board />
  </div>
</template>

<script>
import Board from "./components/Board.vue";

export default {
  components: {
    Board,
  },
};
</script>

<style scoped>
/* CSS styles for the app */
#app {
  display: flex;
  flex-direction: column;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 250px;
  padding: 50px;
  align-items: center;
  box-shadow: 0px 0px 11px 1px rgba(0, 0, 0, 0.14),
    0px 0px 19px 14px rgba(0, 0, 0, 0.03);
  border: 1px solid rgba(0, 0, 0, 0);
  border-radius: 20px;
}

h1 {
  font-size: 36px;
}
</style>
