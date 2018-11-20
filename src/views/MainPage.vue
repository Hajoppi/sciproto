<template>
  <div class="mainpage">
    <div class="title">Tervetuloa</div>
    <p>Aseta ensin omat parametrisi, jotta voimme antaa sinulle parhaan mahdolliset tuen! :-)</p>
    <form>
      <div class="mainpage__field">
        <label for="asd" class="mainpage__label">Asuntotyyppi</label>
        <div class="mainpage__control">
          <label :key="house" :for="house" v-for="house in houses" class="radio">
            <input :value="house" v-model="houseSelected" :id="house" type="radio" class="radio">
            {{house}}
          </label>
        </div>
      </div>
      <div class="mainpage__field">
        <label for="buildYear" class="mainpage__label">Rakennusvuosi</label>
        <div class="mainpage__control">
          <div id="buildYear" class="select is-fullwidth">
            <select v-model="buildYear">
              <option :key="year" v-for="year in years" :value="year">{{year}}</option>
            </select>
          </div>
        </div>
      </div>
      <div class="mainpage__field">
        <label for="residents" class="mainpage__label">Asukkaita</label>
        <div class="mainpage__control">
          <input type="number" class="input" v-model="residents">
        </div>
      </div>
      <div class="mainpage__field">
        <label for="buildYear" class="mainpage__label">Energialuokka</label>
        <div class="mainpage__control">
          <input v-model="energyClass" type="text" class="input" />
        </div>
      </div>
      <div class="mainpage__field">
        <label class="mainpage__label">Sähköauto</label>
        <div class="mainpage__control">
          <label for="electricCar" class="checkbox">
            <input id="electricCar" v-model="electricCar" type="checkbox" class="checkbox">
            Kyllä
          </label>
        </div>
      </div>
      <div class="mainpage__field">
        <label for="asd" class="mainpage__label">Lämmitys</label>
        <div class="mainpage__control">
          <label :for="heatSource" :key="heatSource" v-for="heatSource in heating" class="radio">
            <input :value="heatSource" v-model="heatSelected" :id="heatSource" type="radio" class="radio">
            {{heatSource}}
          </label>
        </div>
      </div>
      <div class="mainpage__field">
        <label class="mainpage__label">Ilmanlämpöpumppu</label>
        <div class="mainpage__control">
          <label for="pump" class="checkbox">
            <input id="pump" v-model="pump" type="checkbox" class="checkbox">
            Kyllä
          </label>
        </div>
      </div>
      <div class="field">
        <div class="control">
          <a class="button" @click="save()">Tallenna</a>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'mainpage',
  data(){
    return {
      houses: [
        'Omakotitalo',
         'Paritalo',
         'Rivitalo',
         'Kerrostalo',
       ],
       heating: [
         "Sähkö",
         "Kaukolämpö",
         "Maalämpö",
         "Öljy",
       ],
       electricCar: false,
       residents: "",
       pump: false,
       energyClass: "",
       houseSelected: "",
       buildYear: 2018,
       heatSelected: "",
    };
  },

  computed: {
    years() {
      const year = new Date().getFullYear();
      return Array.from({length: year - 1900}, (value, index) => 1901 + index).reverse();
    }
  },
  methods: {
    save() {
      this.$router.push({
        name: 'info',
        params: {
          electricCar: this.electricCar,
          residents: this.residents,
          pump: this.pump,
          energyClass: this.energyClass,
          houseSelected: this.houseSelected,
          buildYear: this.buildYear,
          heatSelected: this.heatSelected,
        },
      });
    },
  },
}
</script>
