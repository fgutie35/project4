<script setup>
    import { defineProps, defineEmits } from 'vue';

    const props = defineProps({
        activities: {
            type: Array,
            require: true,
        }
    })

    const emit = defineEmits(['activityDeleted'])

    const deleteActivity = (id) => {
        emit('activityDeleted', id)

    }


</script>

<template>
    <h3>Workout Activity</h3>
    <ul id="list" class="list">
        <li v-for="x in activities" v-bind:key="x.id"
        v-bind:class="x.amount < 0 ? 'minus' : 'plus' ">
        {{ x.text }} <span> hrs:{{ x.amount }}</span>
        <button @click="deleteActivity(x.id)" class="delete-btn">X</button>

        </li>

  
    </ul>

</template>