<script setup>
    import {ref, defineEmits} from 'vue'
    const text = ref('')
    const amount = ref('')

    const emit = defineEmits([
        'activitySubmitted'
    ])

    const onSubmit = () =>{
        const activityData = {
            text: text.value,
            amount: parseFloat(amount.value),
        }

        emit('activitySubmitted', activityData)

        text.value = ''
        amount.value = ''
    }

</script>

<template>

    <h3>Add Activity Hours</h3>
    <form id="form" @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="text">Enter Day of the Week: </label>
            <input type="text" id="text" v-model="text" placeholder="Enter the day: ">
        </div>
        <div class="form-control">
            <label for="amount">Enter Hours: </label>
            <input type="text" id="amount" v-model="amount" placeholder="Enter your hours: ">
        </div>
        <button class="btn">Add Activity</button>

    </form>

</template>