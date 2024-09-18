<script setup>
  import Header from './components/Header.vue';
  import Hours from './components/Hours.vue';
  import ActivityAmount from './components/ActivityAmount.vue';
  import AddHours from './components/AddHours.vue';
  import ActivityList from './components/ActivityList.vue';

  import {ref, computed, onMounted} from 'vue'

  const activities = ref([])

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

  const handleActivity = (activityData) =>{
    activities.value.push({
      id: generateID(),
      text: activityData.text,
      amount: activityData.amount,
    })
    saveToLocalStorage()

  }

const generateID = () =>{
  return Math.floor(Math.random()*10000000)
}

const handleDelete = (id) =>{
  activities.value = activities.value.filter((x) => x.id !== id)
  saveToLocalStorage()
}

const saveToLocalStorage = () => {
    localStorage.setItem('activities', JSON.stringify(activities.value))
  }

onMounted( () => {
  const savedActivities = JSON.parse(localStorage.getItem('activities'))

  if(savedActivities){
    activities.value = savedActivities
  }
})



</script>


<template>

  <Header></Header>
  <div class="container">
    <Hours :total="sum"></Hours>
    <ActivityAmount :hours="hoursIn"></ActivityAmount>
    <AddHours @activitySubmitted="handleActivity"></AddHours>
    <ActivityList :activities="activities" @activityDeleted="handleDelete"></ActivityList>
  </div>



</template>