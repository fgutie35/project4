<script setup>
    import {defineProps} from 'vue'

    const props = defineProps({
        hours: {
            type: Number,
            require: true,
        }
    })

</script>

<template>
    <h4>Your Total Hours</h4>
    <h1 id="hours">{{ hours }}</h1> 

</template>