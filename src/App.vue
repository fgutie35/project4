<script setup>
import Header from './components/Header.vue'
import Hours from './components/Hours.vue'
import ActivityAmount from './components/ActivityAmount.vue';


import {ref, calculated} from 'vue'

const activity = ref([])

const sum = calculated(()=>{
  return activity.value.reduce((acc, x)=>{
    return acc+x.amount
  },0)
})

const hoursIn = calculated(()=>{
    return activity.value
    .filter((x)=>x.amount>0)
    .reduce((acc, x)=>{
      return acc+x.amount
    },0)
  })



</script>

<template>

<Header></Header>
<Hours :total="sum"></Hours>
<ActivityAmount :hours="hoursIn"></ActivityAmount>

</template>