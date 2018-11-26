<template>
  <div class="">
    <router-link :to="{ name: 'main'}">
      <div class="columns">
        <div class="column">
          <message :msg="update()"></message>
        </div>
        <div class="column">
          <message :msg="choose(tips)"></message>
        </div>
      </div>
    </router-link>
  </div>
</template>

<script>
// @ is an alias to /src
import Message from '@/components/Message';
export default {
  name: 'home',
  methods: {
    choose(choices) {
      var index = Math.floor(Math.random() * choices.length);
      return choices[index];
    },
    update() {
      const spending = 2.03;
      const price = 8.74;
      const cost = spending * price;
      const monthAvg = spending - 0.4;
      const monthCost = 8.76;
      return `Eilisen sähkönkulutus ${spending} kW ja hinta ${cost} €.
      Edellisen kuukauden keskiarvo ${monthAvg} kWh ja hinta ${monthCost} €.
      Vastaavien käyttäjien keskiarvo ${monthAvg + 0.5} kWh ja hinta ${9} €.`
    }
  },

  computed: {
    tips() {
      return [
        'Tiesitkö että vaihtamalla sähkölämmityksen ilmalämpöpumppuun voit säästää roimasti sähköä? Vastuksettomat lämpöpumput ovat todella energiatehokkaita!',
        'Lämpimän veden mukana energiaa virtaa suoraan viemäriin! Vältä lutraamasta suihkussa kymmeniä minuutteja ja asenna vettä säästävä suihkupää.',
        'Varmista onko kylpyhuoneesi lattialämmitys rakenteiden kannalta tarpeellinen vai ainoastaan mukavuuden takia asennettu. Tästä mukavuudesta nimittäin joudut pulittamaan kymmeniä euroja vuodessa.',
        'Käytä termostaatteja! Jos lämmitys toimii "laitetaan ikkuna auki kun on kuuma" -periaatteella, menee energiaa hukkaan lähes varmasti yli 500 € vuodessa.',
        'Irtopatterit ovat oikeitä sähkösyöppöjä! Tavallisen lämmittimen jatkuva käyttö voi kuluttaa jopa 5 euron edestä sähköä vuorokaudessa. Talvikauden aikana koko potti voi kasvaa jopa 300 euroon.',
        'Tarkista ilmanvaihtokoneesi teholuokka! Varsinkin vanhoissa taloissa huippuimuri saattaa kuluttaa satoja euroja vuodessa. Ilmastoinnin ei tarvitse olla täydellä teholla muuta kuin ruoanlaiton tai saunomisen aikaan.',
        'Laskemalla sisälämpötilaa asteella, säästät tavallisesti 5% sähkölaskustasi.',
        'Vanha plasma- tai kuvaputkitelevisio kuluttaa todella paljon sähköä LED-televisioon verrattuna! Kannattaakin siis vaihtaa nykyaikaiseen töllöön samantien - saat uuden television ja samalla voitat rahaa!',
        'Tiesitkö, että LED-lamppu kuluttaa vain noin 20% vastaavanlaisen halogeenilampun energiasta. Vaihda LED:eihin nyt ja aloita niistä valoista, jotka ovat useimmin päällä.',
      ];
    }
  },
  components: {
    Message,
  },
}
</script>
