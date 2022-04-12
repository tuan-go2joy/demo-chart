<template>
  <apexchart height="300" :options="options" :series="series"></apexchart>
</template>

<script>
import { defineComponent } from 'vue'
import { getCssVar } from 'quasar'

export default defineComponent({
  name: 'Apexline',
  data () {
    return {
      options: {
        title: {
          text: 'ApexDonut',
          align: 'left'
        },
        chart: {
          id: 'apex-donut',
          type: 'pie'
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
        colors: [getCssVar('primary'), getCssVar('secondary'), getCssVar('negative'), getCssVar('accent')],
        markers: {
          size: 4,
          hover: {
            sizeOffset: 6
          }
        },
        xaxis: {
          categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998]
        }
      },
      series: [30, 40, 45, 50]
    }
  }
})
</script>
