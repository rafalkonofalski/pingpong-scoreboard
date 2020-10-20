<template>
  <header class="scoreboard-header">
    <div class="text-center">
      <div class="scoreboard-label">Pojedynek</div>
    </div>

  </header>
</template>

<script>
export default {
  props: {
    players: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<style>
.scoreboard-label {
  text-transform: uppercase;
  font-size: 19px;
  letter-spacing: 8px;
  padding: 30px 0 50px;
}

.scoreboard-header {
  padding-bottom: 30px;
}

.scoreboard-player {
  text-transform: uppercase;
  font-weight: bold;
  font-size: 30px;
  letter-spacing: 7px;
}
</style>
