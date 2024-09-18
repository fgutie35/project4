<script setup>
    import {defineProps} from 'vue'

    const props = defineProps({
        total: {
            type: Number,
            require: true,
        }
    })

</script>

<template>
    <h4>Your Total Hours</h4>
    <h1 id="hours">{{ total }}</h1> 

</template>