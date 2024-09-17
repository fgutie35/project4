<script setup>
  import Header from './components/Header.vue'
  import Hours from './components/Hours.vue'
  import ActivityAmount from './components/ActivityAmount.vue';
  import AddHours from './components/AddHours.vue';
  import {ref, computed} from 'vue'

  const activities = ref([
    {id: 1, text: 'Monday', amount: 2},
  ])

  const sum = computed(()=>{
    return activities.value.reduce((acc, x)=>{
      return acc+x.amount
    },0)
  })

  const hoursIn = computed(()=>{
    return activities.value
    .filter((x)=>x.amount>0)
    .reduce((acc, x)=>{
      return acc+x.amount
    },0)
  })


</script>



<template>

  <Header></Header>
  <div class="container">
    <Hours :total="sum"></Hours>
    <ActivityAmount :hours="hoursIn"></ActivityAmount>
    <AddHours></AddHours>
  </div>



</template>