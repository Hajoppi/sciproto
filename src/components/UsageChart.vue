<script>
import { Doughnut, mixins } from 'vue-chartjs';
const { reactiveProp } = mixins;
export default {
  name: 'UsageChart',
  extends: Doughnut,
  props:  ['options', 'data'],
  mixins: [reactiveProp],
  data(){
    return {
    };
  },
  mounted() {
    this.renderChart(this.chartData, this.options);
  },
};
</script>
