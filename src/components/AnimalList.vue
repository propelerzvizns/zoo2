<template>
  <div class="hello">
    <form @submit.prevent>
      <input type="text" v-model="sort"/>
      <input type="text" v-model="name"/>
      <input type="date" v-model="dateOfBirth"/>
      <select v-model="selected">
        <option v-for="(animalSeletor, index) in animalSeletors" :key="index" :value="animalSeletor">{{animalSeletor}}</option>
      </select>
       <button @click="addAnimal">add animal</button>

    </form>
   <table>
     <tr>
       <th>sort</th>
       <th>name</th>
       <th>date of birth</th>
       <th>sector</th>
       <th></th>
       <th></th>
     </tr>
     <tr v-for="(animal, index) in animals" :key="index">
       <td>{{animal.sort}}</td>
       <td>{{animal.name}}</td>
       <td v-if="animal.dateOfBirth">{{animal.dateOfBirth.toLocaleString()}}</td>
       <td v-else>unknown</td>
       <td>{{animal.animalSeletor}}</td>
       <td><button @click="remove(index)">delete</button></td>
       <td><button @click="moveToTop(index, animal)">move to top</button></td>
    
     </tr>
   </table>
  <table>
    <tr>
      <th>name of sector</th>
      <th></th>
    </tr>
    <tr v-for="(sector, index) in animalSeletors" :key="index"> 
     <td>{{sector}}</td>
     <td><button @click="listAnimals(sector)">vidi listu zivotinja</button></td>
    </tr>
  </table>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',

  data() {
    return {
      sort: '',
      name: '',
      dateOfBirth: null,
      selected: '',
      animalSeletors: ['bird', 'snake', 'boar'],
      animals: [
        {
          sort: 'dog',
          name: 'cuko',
          dateOfBirth: new Date(2020, 1, 7),
        },        
        {
          sort: 'wolf',
          name: 'vucko',
          dateOfBirth: new Date(2011, 11, 27),
        },        
        {
          sort: 'bird',
          name: 'birdie',
          dateOfBirth: new Date(2022, 12, 17),
        },        
        {
          sort: 'pig',
          name: 'pigic',
          dateOfBirth: new Date(2012, 4, 25),
        },       
        {
          sort: 'cat',
          name: 'maca',
          dateOfBirth: null
        },
      ]

    }
  },
  methods: {
    remove(index){
      this.animals.splice(index, 1);
    },

    moveToTop(index, animal) {
      this.remove(index);
      this.animals.unshift(animal);
    },
    addAnimal() {
      var newAnimal = {
        name: this.name,
        sort: this.sort,
        dateOfBirth: this.dateOfBirth,
        animalSeletor: this.selected
      }
     this.animals.push(newAnimal);
    },
   
    listAnimals(sector) {
      const animalsList=[];
     this.animals.forEach(animal => {
       if(animal.animalSeletor === sector){
         animalsList.push(`Animal name: ${animal.name}, Animal sort: ${animal.sort}, Date of birth:${animal.dateOfBirth} | END OF ITEM | `);

       }
  
      
     });
     alert(animalsList.toString());
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 30%;
  margin-left: 35%;
  margin-right: 35%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
form {
  display: flex;
  flex-direction: column;
  width: 30%;
  margin-left: 35%;
  margin-right: 35%;
}

</style>
