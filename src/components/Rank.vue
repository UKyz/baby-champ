<template>
  <div>
    <h2>Classement</h2>
    <v-data-table
      :headers="headersTable"
      :items="players"
      class="elevation-1"
      :sort-by.sync="sortBy"
      :sort-desc.sync="sortDesc"
    ></v-data-table>
  </div>
</template>

<script>
export default {
  name: 'Rank',
  data () {
    return {
      headersTable: [
        {
          text: 'Nom',
          value: 'name'
        },
        {
          text: 'Points',
          value: 'points'
        },
        {
          text: 'Grade',
          value: 'grade'
        }
      ],
      sortBy: 'points',
      sortDesc: true,
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
      gradePoint: 250,
      gradesRank: ['Bronze 2', 'Bronze 1', 'Silver 2', 'Silver 1', 'Gold 2', 'Gold 1', 'Platinium 2', 'Platinium 1']
    }
  },
  methods: {
    addGrade () {
      this.players.forEach(player => {
        player.grade = this.gradesRank[parseInt((player.points - 1) / this.gradePoint)]
      })
    }
  },
  mounted () {
    this.addGrade()
  }
}
</script>

<style scoped>

</style>
