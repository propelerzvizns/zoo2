<template>
  <div class="hello">
   <table>
     <tr>
       <th>sort</th>
       <th>name</th>
       <th>date of birth</th>
       <th></th>
     </tr>
     <tr v-for="(animal, index) in animals" :key="index">
       <td>{{animal.sort}}</td>
       <td>{{animal.name}}</td>
       <td v-if="animal.dateOfBirth">{{animal.dateOfBirth.toLocaleString()}}</td>
       <td v-else>unknown</td>
       <td><button @click="remove(index)">delete</button></td>
    
     </tr>
   </table>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data() {
    return {
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
</style>
