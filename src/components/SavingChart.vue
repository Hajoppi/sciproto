<script>
import { Bar, mixins } from 'vue-chartjs';
const { reactiveProp } = mixins;
export default {
  name: 'SavingChart',
  extends: Bar,
  props:  ['options', 'data'],
  mixins: [reactiveProp],
  data(){
    return {
    };
  },
  mounted() {
    this.renderChart(
      this.chartData,
      {
        scales: {
          yAxes: [{
            ticks: {
              beginAtZero: true,
              fontSize: 15,
            },
          }],
          xAxes: [{
            ticks: {
              fontSize: 12,
            }
          }],
        },
        legend: {
          labels: {
            fontSize: 15,
          },
        },
      },
    );
  },
}
</script>
