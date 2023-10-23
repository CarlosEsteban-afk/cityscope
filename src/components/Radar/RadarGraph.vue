<template>
    <Radar :data="props.charData" :options="props.charOptions" :key="chartKey" />
</template>
  
<script setup>

import {
    Chart as ChartJS,
    RadialLinearScale,
    PointElement,
    LineElement,
    Filler,
    Tooltip,
    Legend
} from 'chart.js'
import { computed } from 'vue';

import { Radar } from 'vue-chartjs'

ChartJS.register(
    RadialLinearScale,
    PointElement,
    LineElement,
    Filler,
    Tooltip,
    Legend
)
const props = defineProps({
    charData: {
        type: Object,
        required: true,
    },
    charOptions: {
        type: Object,
        required: false,
        default: () => { }
    },
    chartKey: {
        type: Number,
        required: false
    }

});
/**
 * 

 */



</script>