<template>
  <apexchart height="300" type="bar" :options="options" :series="series" />
  <q-btn color="primary" icon="check" label="111111" @click="onClick" />
</template>

<script>
import { defineComponent } from 'vue'
// import { getCssVar } from 'quasar'

export default defineComponent({
  name: 'ApexColumn',
  data () {
    return {
      arr: {
        1: '1',
        2: '2',
        3: '3',
        4: '4',
        5: '5',
        6: '6',
        7: '7'
      },
      options: {
        chart: {
          type: 'bar',
          height: 350,
          stacked: true,
          toolbar: {
            show: true
          },
          zoom: {
            enabled: true
          }
        },
        tooltip: {
          enabled: true,
          custom: ({ series, seriesIndex, dataPointIndex, w }) => {
            return '<div class="arrow_box">' +
              ' <p> total: 400,000 </p>' +
              ' <p> a: 300,000 </p>' +
              ' <p> b: 100,000 </p>' +
              '</div>'
          }
        },
        responsive: [{
          breakpoint: 480,
          options: {
            legend: {
              position: 'bottom',
              offsetX: -10,
              offsetY: 0
            }
          }
        }],
        plotOptions: {
          bar: {
            horizontal: false,
            borderRadius: 10
          }
        },
        xaxis: {
          type: 'category',
          category: []
        },
        legend: {
          position: 'right',
          offsetY: 40
        },
        fill: {
          opacity: 1
        }
      },
      series: [{
        name: 'PRODUCT A',
        data: [44, 55, 41, 67, 22, 43]
      }, {
        name: 'PRODUCT B',
        data: [13, 23, 20, 8, 13, 27]
      }]
    }
  },
  methods: {
    onClick () {
      this.options = {
        ...this.options,
        ...{
          xaxis: {
            category: this.arr
          }
        }
      }
      this.series = [
        {
          name: 'PRODUCT A',
          data: [44, 55, 41, 67, 22, 43, 44]
        }, {
          name: 'PRODUCT B',
          data: [13, 23, 20, 8, 13, 27, 13]
        }
      ]
    }
  }
})
</script>
