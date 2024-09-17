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

<div class="act-amnt">
        <div>
            <h3>Hours added</h3>
            <p id="hours-plus" class="hours plus"> {{ hours }}</p>
        </div>
    </div>

</template>