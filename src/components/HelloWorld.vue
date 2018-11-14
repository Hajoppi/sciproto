<template>
  <div class="proto has-background-primary">
    <div class="hero">
      <div class="hero-body header">
          <i class="fa fa-bars fa-2x burgeri"
            :style="{color: activeColor}"
            @click="activeColor = randomColors(); modal = true;"></i>
          <span class="title is-white">
          Sähkösi
        </span>
      </div>
    </div>
    <div class="card graph" v-if="show" @click="show = false">
        <div class="card-content text">
          <div>Pirteää perjantaihuomenta! 😊🌻<br><br>
Eilisen sähkönkulutus <b>16,12 kWh</b> ja hinta <b>2,07€.</b><br>
Edellisen kuukauden keskiarvo <b>14,35 kWh</b> ja <b>1,81€.</b><br>
Vastaavien käyttäjien keskiarvo <b>15,51 kWh</b> ja <b>1,95€.</b><br>
<br>
Kuukauden keskiarvosi on edelleen top 20% joukossa! Hyvin menee! ⚡️🏅</div>
      </div>
    </div>
    <div class="card graph">
        <div class="card-content">
          <img src="../assets/graph.jpg"/>
      </div>
    </div>
    <div class="card graph">
        <div class="card-content">
          <div>Tähän astinen kulutuksesi {{elec}} kwh</div>
      </div>
    </div>
    <div class="card graph">
        <div class="card-content">
          Tähänastinen säästötavoitteesi
          <p></p>
          <progress class="progress" :value="progress" max="100">15%</progress>
      </div>
    </div>
    <div class="modal" :class="{'is-active': modal}">
      <div class="modal-background"></div>
        <div class="modal-content">
          <p class="image">
            <img src="../assets/mainos1.jpg" alt="">
          </p>
        </div>
        <button class="modal-close is-large" aria-label="close" @click="modal = false"></button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      elec: 1,
      progress: 0,
      show: true,
      activeColor: '#FFF',
      modal: false,
    };
  },
  mounted() {
    setInterval(() => {
      this.elec += 0.1;
      this.progress += 1;
    },1000);
  },

  methods: {
    randomColors() {
      return '#' + Math.floor(Math.random() * 16777215).toString(16);
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.graph {
  margin: 1em;
}
.header {
  padding: 1.5rem 1.5rem 0.1rem;
}
.is-white {
  display: block;
  float:center;
  color: white;
}
.text {
  text-align: left;
}
.burgeri {
  display: block;
  float: left;
  color: white;
}

b {
  color: #d1ad26;
}
</style>
