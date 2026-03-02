<script setup>
import { computed, ref } from 'vue';

const people = ref([
  {
    name: 'Jan', age: 12
  },
  {
    name: 'piet', age: 20
  }
])


const newName = ref("")
const newAge = ref()
const children = computed(() => people.value.filter(person => person.age <= 17));
const adults = computed(() => people.value.filter(person => person.age > 17));

const totalPeople = computed(() => {return people.value.length});
const totalAdults = computed(() => {return adults.value.length});
const totalChildren = computed(() => {return children.value.length});

const addPerson = () => {
  people.value.push({name :  newName.value, age : newAge.value});  
  newName.value = "";
  newAge.value = "";
}


</script>

<template>
  <div>
    <h3>lijst van personen</h3>
    <input type="text" v-model="newName" placeholder="Name">
    <input type="number" v-model.number="newAge" placeholder="Age">
    <button @click="addPerson">Toevoegen</button>

    <ul>
      <h2>personen</h2>
      <li v-for="(person, index) in people" :key = "index">
        {{ person.name }} : {{ person.age }}
      </li>
      <br>
      <h2>kinderen</h2>
      <li v-for="(child, index) in children" :key = 'index'>
        {{ child.name }} : {{child.age}}
      </li>
      <br>      
       <h2>Volwassenen</h2> 
      <li v-for="(adult, index) in adults" :key = 'index'>
        {{ adult.name }} : {{adult.age}}
      </li>
      <br>
      <h2>totalen</h2>
      <li>
        Personen : {{ totalPeople }} Volwassenen  : {{ totalAdults }} kinderen: {{ totalChildren }}
      </li>
    </ul>


  </div>

</template>

<style scoped>



</style>
