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
            <h4>Hours added</h4>
            <p id="hours-plus" class="hours plus"> {{ hours }}</p>
        </div>
    </div>

</template>