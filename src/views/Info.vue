<template>
  <div class="">
    <div class="columns is-multiline">
      <div class="column is-one-third">
        <div class="chart-card">
          <saving-chart :chart-data="dataCollection"></saving-chart>
        </div>
      </div>
      <div class="column is-one-third">
        <div class="chart-card">
          <usage-chart
            :chart-data="usageCollection"
            :options="usageOptions">
          </usage-chart>
        </div>
      </div>
      <div class="column is-one-third">
        <div class="chart-card">8,45kwh</div>
      </div>
      <div class="column is-one-third">
        <progress class="progress is-large" value="15" max="100"></progress>
        <div class="spend-label">Säästötavoitteesi</div>
      </div>
    </div>
    <div class="modal" :class="{ 'is-active': showModal }">
      <div class="modal-background"></div>
      <button class="modal-close is-large" aria-label="close" @click="showModal = false"></button>
      <section class="modal-content">
        <usage-chart :chart-data="modalCollection"></usage-chart>
      </section>
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
      dataCollection: null,
      usageCollection: null,
      modalCollection: null,
      showModal: false,
      usageOptions: {
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
        onClick: (a,chart) => {
          if(chart[0]){
            this.fillModalCollection(chart[0]._model.label);
            this.showModal = true;
          }
        }
      },
    };
  },
  methods: {
    getFactor() {
      var factor = 1;
      const params = this.$route.params;
      const houseParams = {
        'Omakotitalo': 1,
        'Paritalo': 0.9,
        'Rivitalo': 0.9,
        'Kerrostalo': 0.5,
      }

      factor *= houseParams[params.houseSelected];
      factor *= 2020 / params.buildYear;
      factor *= parseInt(params.residents)/4;
      return factor;
    },
    fillModalCollection(category) {
      this.modalCollection = {
        labels: [
          'Osuus 1',
          'Osuus 2',
          'Osuus 3',
          'Osuus 4',
        ],
        datasets: [
          {
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
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
      switch (category) {
        case 'Lämmitys':
          this.modalCollection.labels = [
            'Sähkölämmitys',
          ];
          this.modalCollection.datasets[0].data =
            this.modalCollection.datasets[0].data.slice(0,1);
          break;
        case 'Kodinkoneet':
          this.modalCollection.labels = [
            'Tiskikone',
            'Pesukone',
            'Jääkaappi',
            'Pakastin',
          ];
          break;
        case 'Valaistus':
          this.modalCollection.labels = [
            'Eteinen',
            'Keittiö',
            'Olohuone',
            'Makuuhuone',
          ];
          break;
        case 'Viihde-elektroniikka':
          this.modalCollection.labels = [
            'Televisio',
            'Tietokone 1',
            'Tietokone 2',
            'Konsoli'
          ];
          break;
        case 'Sähköauto':
          this.modalCollection.labels = [
            'Tesla Model S'
          ];
          this.modalCollection.datasets[0].data =
            this.modalCollection.datasets[0].data.slice(0,1);
          break;
        default:

      }
    },
    fillData () {
      this.dataCollection = {
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
            label: 'Säästö',
            backgroundColor: 'blue',
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
            type: 'line',
            fill: 'false',
            pointRadius: 8,
            borderWidth: 10,
          },
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

        ],
      };
      this.usageCollection = {
        labels: [
          'Kodinkoneet',
          'Valaistus',
          'Viihde-elektroniikka',
          'Sähköauto',
        ],
        datasets: [
          {
            data: [100, 20, 40, 130],
            borderWidth: 0,
            backgroundColor: [
                'red',
                'blue',
                'green',
                'magenta',
                'yellow',
            ],
          },
        ],
      };
      if(this.$route.params.heatSelected === "Sähkö"){
        this.usageCollection.labels.push("Lämmitys");
        this.usageCollection.datasets[0].data.push(230);
      }
    },
    getRandomInt () {
      return (Math.floor(Math.random() * (50 - 5 + 1)) + 5) * this.getFactor()
    }
  },
  components: {
    SavingChart,
    UsageChart,
  },
}
</script>
