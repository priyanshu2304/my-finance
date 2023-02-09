<template>
  <div>
    <div :id="chartId"></div>
  </div>
</template>

<script>
import Highcharts from 'highcharts'
export default {
  name: 'PieChart',
  props: ['chartId', 'title', 'seriesData'],
  mounted() {
    console.log('seriesData', this.seriesData)
    Highcharts.chart(this.chartId, {
      chart: {
        type: 'pie',
      },
      title: {
        text: this.title,
      },
      plotOptions: {
        pie: {
          allowPointSelect: true,
          cursor: 'pointer',
          dataLabels: {
            enabled: true,
            format: '<b>{point.name}</b>: {point.percentage:.1f} %',
          },
        },
      },
      series: [
        {
          name: this.title,
          data: this.seriesData,
        },
      ],
    })
  },
}
</script>
