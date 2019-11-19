<template>
  <div>
    <table>
      <tr>
        <th>Species:</th>
        <th>Name:</th>
        <th>Age:</th>
      </tr>
      <tr v-for="(animal,index) in animals" :key="index">
        <td>{{ animal.species }}</td>
        <td>{{ animal.name }}</td>
        <td>{{ animal.dateOfBirth }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  data () {
      return {
          animals: [
            {species: 'Lion', name: 'Simba', dateOfBirth: moment().format("DD-MM-YYYY")},
            {species: 'Parrot', name: 'Ricky', dateOfBirth: moment().format("DD-MM-YYYY")},
            {species: 'Penguin', name: 'Noot', dateOfBirth: moment().format("DD-MM-YYYY")},
            {species: 'Penguin', name: 'Noot-Noot', dateOfBirth: moment().format("DD-MM-YYYY")},
            {species: 'Rhino', name: 'Carl', dateOfBirth: moment().format("DD-MM-YYYY")}
          ]
        }

    }
}

</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

table {
  margin-left:auto;
  margin-right:auto;
  border-collapse: collapse;
}

table, th, td {
  border: 1px solid black;
}
</style>
