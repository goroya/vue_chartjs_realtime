<template>
  <div class="small">
    <line-chart :chart-data="dataPoints"></line-chart>
    <button @click="fillData()">Randomize</button>
  </div>
</template>

<script>
  import LineChart from './LineChart'

  export default {
    components: {
      LineChart
    },
    data () {
      return {
        num: 0,
        dataPoints: null,
        labels: [],
        sample: []
      }
    },
    mounted () {
      this.fillData()
      setInterval(() => {
        this.num++
        this.labels.push(this.num)
        this.sample.push(this.getRandomInt())
        this.fillData()
      }, 2000)
    },
    methods: {
      getRandomInt () {
        return Math.floor(Math.random() * (50 - 5 + 1)) + 5
      },
      fillData () {
        this.dataPoints = {
          labels: this.labels,
          datasets: [
            {
              label: 'Data One',
              backgroundColor: '#f87979',
              data: this.sample
            }
          ]
        }
      }
    }
  }
</script>

<style lang="scss">
  .small {
    max-width: 600px;
    margin:  150px auto;
  }
</style>
