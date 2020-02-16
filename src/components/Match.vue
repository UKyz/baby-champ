<template>
  <div>
  <h2>Ajouter un match</h2>
    <v-container>
      <v-row>
        <v-col cols="12">
          <v-select v-model="gameTypesChoice" :items="gameTypes" label="Type de match"/>

          <v-divider></v-divider>

          <div v-if="gameTypesChoice">
            <v-row>
              <v-col cols="12" sm="6" class="d-flex align-center">
                <v-select v-model="player11" :items="playersName" label="Joueur 1"/>
              </v-col>
              <v-col cols="12" sm="6" class="d-flex align-center">
                <v-select v-model="player21" :items="playersName" label="Joueur 2"/>
              </v-col>
            </v-row>
          </div>

          <div v-if="gameTypesChoice === '2v2'">
            <v-row>
              <v-col cols="12" sm="6" class="d-flex align-center">
                <v-select v-model="player12" :items="playersName" label="Joueur 3"/>
              </v-col>
              <v-col cols="12" sm="6" class="d-flex align-center">
                <v-select v-model="player22" :items="playersName" label="Joueur 4"/>
              </v-col>
            </v-row>
          </div>

          <div v-if="gameTypesChoice">
            <v-row>
              <v-col cols="12" sm="6" class="d-flex align-center">
                <v-text-field v-model="score1" type="number" label="Score 1"/>
              </v-col>
              <v-col cols="12" sm="6" class="d-flex align-center">
                <v-text-field v-model="score2" type="number" label="Score 2"/>
              </v-col>
            </v-row>
          </div>
        </v-col>

        <v-col>
          <v-btn ref="button" color="primary" @click="addGame">
            Ajouter le match
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Match',
  data () {
    return {
      gameTypes: ['1v1', '2v2'],
      gameTypesChoice: null,
      player11: null,
      player12: null,
      player21: null,
      player22: null,
      score1: 0,
      score2: 0,
      players: [
        {
          id: 1,
          name: 'Victor',
          points: 2000
        },
        {
          id: 2,
          name: 'Maxime',
          points: 1
        },
        {
          id: 3,
          name: 'Davy',
          points: 1251
        },
        {
          id: 4,
          name: 'Nico',
          points: 1840
        }
      ],
      playersName: []
    }
  },
  methods: {
    addGame () {
      const game = {
        player1: this.player11,
        player2: this.player21,
        score1: this.score1,
        score2: this.score2
      }
      if (this.gameTypesChoice === '2v2') {
        game.player3 = this.player12
        game.player4 = this.player22
      }
      console.log(game)
    },
    getPlayersName () {
      const tabPlayers = []
      this.players.forEach(player => {
        tabPlayers.push({
          value: player.id,
          text: player.name
        })
      })
      return tabPlayers
    }
  },
  mounted () {
    this.playersName = this.getPlayersName()
  }
}
</script>

<style scoped>

</style>
