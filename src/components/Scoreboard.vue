<template>
  <div class="scoreboard">
    <ScoreboardHeader :players="players" />
    <ScoreboardBody :players="players" :winnerName="winner" @point="updateScore" />
  </div>
</template>

<script>
import ScoreboardHeader from './ScoreboardHeader'
import ScoreboardBody from './ScoreboardBody'

export default {
  components: {
    ScoreboardHeader,
    ScoreboardBody
  },

  data() {
    return {
      players: [
        {
          id: 0,
          name: 'Paulina',
          score: {
            gems: 0,
            sets: 0
          }
        },
        {
          id: 1,
          name: 'Olaf',
          score: {
            gems: 0,
            sets: 0
          }
        }
      ],
      winner: ''
    }
  },

  methods: {
    updateScore(id) {
      this.players.forEach((player) => {
        if (player.id === id) {
          this.rules(player.score, player.id)
        }
      })
    },

    rules(scoreObj, playerId) {
      if (scoreObj) {
        if (scoreObj.gems < 11) {
          scoreObj.gems++
        } else {
          this.players.forEach((player) => {
            player.score.gems = 0
          })

          scoreObj.sets++

          if (scoreObj.sets >= 2) {
            this.setWinner(playerId)
            window.removeEventListener('keydown')
          }
        }
      }
    },

    setWinner(playerId) {
      this.winner = `Zwycięzcą zostaje ${this.players[playerId].name}`
    }
  }
}
</script>

<style></style>
