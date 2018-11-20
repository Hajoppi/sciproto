<template>
  <div class="container">
    <section class="hero">
      <h1 class="hero-body has-text-white">Sähkösi</h1>
    </section>
    <div class="columns is-multiline">
      <div class="column is-one-third">
        <div class="chart-card">
          <saving-chart :chart-data="datacollection"></saving-chart>
        </div>
      </div>
      <div class="column is-one-third">
        <div class="chart-card">
          <usage-chart :chart-data="usagecollection"></usage-chart>
        </div>
      </div>
      <div class="column is-one-third">
        <div class="chart-card">8,45kwh</div>
      </div>
      <div class="column is-one-third">
        <div class="chart-card">Säästötavoitteesi</div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import SavingChart from '@/components/SavingChart';
import UsageChart from '@/components/UsageChart';

export default {
  name: 'info',
  mounted () {
    this.fillData();
  },
  data() {
    return {
      datacollection: null,
      usagecollection: null,
    };
  },
  methods: {
    fillData () {
      this.datacollection = {
        labels: [
          'Kesäkuu',
          'Heinäkuu',
          'Elokuu',
          'Syyskuu',
          'Lokakuu',
          'Marraskuu',
        ],
        datasets: [
          {
            label: 'Sähkönkulutus',
            backgroundColor: 'green',
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ]
          },
          {
            label: 'Säästö',
            backgroundColor: 'blue',
            data: [
              10,
              20,
              30,
              40,
              50,
              60,
            ],
            type: 'scatter',
            fill: 'false',
          },
        ],
      };
      this.usagecollection = {
        labels: [
          'Lämmitys',
          'Sähkölaitteet',
          'Dankit meemut',
          'Lorem Ipsum',
        ],
        datasets: [
          {
            data: [10,20,30,40],
            borderWidth: 0,
            backgroundColor: [
                'red',
                'blue',
                'green',
                'magenta',
            ],
          },
        ],
      };
    },
    getRandomInt () {
      return Math.floor(Math.random() * (50 - 5 + 1)) + 5
    }
  },
  components: {
    SavingChart,
    UsageChart,
  },
}
</script>
