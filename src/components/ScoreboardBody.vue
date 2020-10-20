<template>
  <header class="scoreboard-body">
    <div class="flex">
      <div class="flex-col text-center">
        <div class="scoreboard-player scoreboard-player--left">{{ players[0].name }}</div>
      </div>
      <div class="flex-col text-center">
        <div class="scoreboard-player scoreboard-player--right">{{ players[1].name }}</div>
      </div>
    </div>
    <div class="flex flex-space-around">
      <div class="flex-col flex-col-min">
        <div class="scoreboard-set scoreboard-set--left">
          {{ players[0].score.sets }}
        </div>
      </div>
      <div class="flex-col flex-col-40pc text-center">
        <div class="scoreboard-value noselect" @click="addPointTo(players[0].id)">{{ players[0].score.gems }}</div>
      </div>
      <div class="flex-col flex-col-40pc text-center">
        <div class="scoreboard-value noselect" @click="addPointTo(players[1].id)">{{ players[1].score.gems }}</div>
      </div>
      <div class="flex-col flex-col-min">
        <div class="scoreboard-set scoreboard-set--right">
          {{ players[1].score.sets }}
        </div>
      </div>
    </div>
    <teleport to="body">
      <div v-if="winnerName" class="summary">
        {{ winnerName }}
      </div>
    </teleport>
  </header>
</template>

<script>
export default {
  name: 'ScoreboardBody',
  props: {
    players: {
      type: Array,
      default: () => []
    },

    winnerName: {
      type: String,
      default: ''
    }
  },

  methods: {
    addPointTo(playerId) {
      this.$emit('point', playerId)
    },

    keypressHandle() {
      window.addEventListener('keydown', (e) => {
        console.log('pressed', e.keyCode)
        if (e.keyCode === 37) {
          this.addPointTo(0)
        }

        if (e.keyCode === 39) {
          this.addPointTo(1)
        }
      })
    }
  },

  mounted() {
    this.keypressHandle()
  }
}
</script>

<style lang="scss">
.scoreboard-player {
  text-transform: uppercase;
  font-size: 44px;
  letter-spacing: 8px;

  &--left {
    padding-left: 40px;
  }

  &--right {
    padding-right: 40px;
  }
}

.scoreboard-body {
  font-family: Teko, sans-serif;
  padding: 0 25px;
  line-height: 1;
}

.scoreboard-set {
  font-size: 18px;
  font-weight: bold;

  &--left,
  &--right {
    font-size: 80px;
    padding: 20px 0;
  }

  &--left {
    text-align: left;
  }

  &--right {
    text-align: right;
  }
}

.scoreboard-value {
  font-size: 23rem /* 440/16 */;
  font-weight: normal;
  text-align: center;
  border: 1px solid black;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.4);
  max-width: 80%;
  margin: 0 auto;
  padding: 50px 0 20px;
}

.summary {
  text-align: center;
  font-size: 30px;
  text-transform: uppercase;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.8);
}

.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none; /* Safari */
  -khtml-user-select: none; /* Konqueror HTML */
  -moz-user-select: none; /* Old versions of Firefox */
  -ms-user-select: none; /* Internet Explorer/Edge */
  user-select: none; /* Non-prefixed version, currently
                        supported by Chrome, Edge, Opera and Firefox */
}
</style>
