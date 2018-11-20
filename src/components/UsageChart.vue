<script>
import { Doughnut, mixins } from 'vue-chartjs';
const { reactiveProp } = mixins;
export default {
  name: 'SavingChart',
  extends: Doughnut,
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
        color: [
          'red',
          'blue',
          'green',
          'magenta',
        ],
        legend: {
          labels: {
            fontSize: 15,
          },
        },
      },
    );
  },
};
</script>
