<template>
  <Scoreboard />
</template>

<script>
import Scoreboard from './components/Scoreboard.vue'

export default {
  name: 'App',
  components: {
    Scoreboard
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Teko:wght@300&display=swap');

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  font-family: Helvetica, sans-serif;
  background-color: rgb(228, 228, 228);
}

.flex {
  display: flex;
}

.flex-col {
  flex: 1;
}

.flex-col-min {
  flex: auto;
  max-width: 40px;
}

.flex-space-around {
  justify-content: space-around;
}

flex-col-40pc {
  max-width: 40%;
}

.text-center {
  text-align: center;
}
</style>
