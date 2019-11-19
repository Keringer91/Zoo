<template>
  <div>

     <form @submit.prevent>
       <table>
        <tr>
          <td><label>Species:</label></td>
          <td><input v-model="newAnimal.species" type="text" id="species"></td>
        </tr>
        <tr>
          <td><label>Animal's name:</label></td>
          <td><input v-model="newAnimal.name" type="text" id="name"></td>
        </tr>
        <tr>
          <td><label>Date of birth:</label></td>
          <td><input v-model="newAnimal.dateOfBirth" type="text" id="dateOfBirth"></td>
        </tr>
      </table>  
      <button @click="addNewAnimal" type="submit">Submit</button>
    </form> 
  
    <table>
      <tr>
        <th>Species:</th>
        <th>Name:</th>
        <th>Age:</th>
      </tr>
      <tr v-for="(animal,index) in animals" :key="index">
        <td>{{ animal.species }}</td>
        <td>{{ animal.name }}</td>
        <td>{{ animal.dateOfBirth ? animal.dateOfBirth : 'Unknown' }}</td>
        <td> <button @click="RemoveAnimal(index)">Remove Animal</button></td>
        <td> <button @click="MoveToTop(index)">Move to top</button></td>
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
              {species: 'Penguin', name: 'Noot-Noot', dateOfBirth: ''},
              {species: 'Rhino', name: 'Carl', dateOfBirth: moment().format("DD-MM-YYYY")}
            ],
            newAnimal: {}
          }
  },

    methods: {
       RemoveAnimal(key) {
        this.animals.splice(key, 1);
      },

       MoveToTop(key) {   
        this.animals.unshift(this.animals.splice(key, 1)[0]);
      },

      addNewAnimal(){
        this.animals.push({...this.newAnimal});
        this.newAnimal = {};
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
