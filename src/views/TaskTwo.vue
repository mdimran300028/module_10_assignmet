<script setup>
import {ref, onMounted, onBeforeUnmount} from "vue";
const newItem = ref(16)
let chart = null

const dataset = [
    300,50,100
]

const data = {
  labels:[
      'Red','Blue','Yellow'
  ],
  datasets:[{
    label:'My First Dataset',
    data: dataset,
    backgroundColor: [
        'rgb(255,99,132)',
        'rgb(54,162,235)',
        'rgb(255,205,86)',
        'rgb(43,105,86)',
        'rgb(21,21,186)',
    ],
    hoverOffset:4
  }]
}

const config = {
  type:'doughnut',data:data
}

onMounted(()=>{
  const ctx = document.getElementById('myChart')
  chart = new Chart(ctx, config)
})

function updateChart(){
  dataset.push(newItem.value)
}

onBeforeUnmount(()=>{
  dataset.length = 0
  data.length = 0
  config.length = 0
  chart = null
})
</script>

<template>
  <h3 class="text-center fw-bold my-2">Task-2: Pie chart</h3>
  <div class="chart">
    <canvas id="myChart"></canvas>
  </div>

</template>

<style scoped>
.chart{
  box-sizing: border-box;
  width: 500px;
  height: 500px;
  margin: auto auto;
  background-color: #888888;
}
</style>
