
<template>
    <div class="padding-wrapper">

        <RadarGraph :charData="data" :charOptions="options" :chartKey="key" />


    </div>
</template>

<script setup>
import RadarGraph from './RadarGraph.vue'



const data = {
    labels: ['Salud', 'Movilidad', 'Educación', 'Deporte', 'Cultura', 'Áreas verdes'],
    datasets: [
        {
            label: 'Estado actual',
            backgroundColor: 'rgba(0, 119, 204, 0.2)',
            borderColor: 'rgba(0, 119, 204, 1)',
            pointBackgroundColor: 'rgba(0, 119, 204, 1)',
            pointBorderColor: '#fff',
            pointHoverBackgroundColor: '#fff',
            pointHoverBorderColor: 'rgba(0, 119, 204, 1)',
            data: [5, 4, 3, 6, 7, 8]
        },
        {
            label: 'Estado deseado',
            backgroundColor: 'rgba(204, 0, 0, 0.2)',
            borderColor: 'rgba(204, 0, 0, 1)',
            pointBackgroundColor: 'rgba(204, 0, 0, 1)',
            pointBorderColor: '#fff',
            pointHoverBackgroundColor: '#fff',
            pointHoverBorderColor: 'rgba(204, 0, 0, 1)',
            data: [7, 8, 9, 6, 8, 8]
        }
    ]
};

const options = {

    responsive: true,
    maintainAspectRatio: false,
    legend: {
        position: 'bottom' // Position labels on the side
    },
    scale: {
        ticks: {
            beginAtZero: true,
            max: 10
        }
    },

    pointLabels: {
        fontSize: 12,
        fontColor: 'rgba(0, 0, 0, 0.7)',
        fontStyle: 'bold',
        pointLabelPlacement: 'bottom' // Position labels on the side
    }
};
const key = 0;


function randomizeData() {
    this.data.datasets.forEach(dataset => {
        dataset.data = dataset.data.map(() => getRandomValue());
    });
    this.chartKey += 1; // Incrementar la propiedad key para forzar la actualización del componente RadarGraph
}

function getRandomValue() {
    return Math.floor(Math.random() * 10) + 1; // Generar un número aleatorio entre 1 y 10
}


</script>


<style>
.padding-wrapper {
    padding: 16px;
}
</style>