<script>
export default {
  data() {
    return {
      checkedNames: [],
      names:[
        "Zaspal na prednaske?",
        "Vynechal skolu na tyzden?",
        "Prisiek az po polovici prednasky?",
        "Odisiel z cvika hned po ziskani bodu?",
        "Submitol zly file projektu?",
        "Odovzdal plagiat?",
        "Zacal projekt (menej) 24 hodin pred odovzdavanim?",
        "Skippol polsemestralku?",
        "Urobil IMA2 skor ako IMA1?",
        "Mal 4 matiky v jednom semestri?",
        "Podal falosnu prekazku v studiu?",
        "Dostal sa do 3BIT+?",
        "Zhodil Merlina/Evu?",
        "Zaregistroval si 2 prekryvajuce sa cvika?",
        "Rozbil pohar v kachne?",
        "Omylom podal OZNUK?",
        "Nadaval na garanta v public chanelli?",
        "Nabural do nejakeho garanta predmetu?",
        "Pohadal sa s vazenym doktorom Fuchsom?",
        "Rozosmial celu D105?",
        "Mal mobil vo vrecku pocas skusky?",
        "Dosiahol presne minimum na E?",
        "Presiel predmet bez pritomnosti na jedinej prednaske?",
        "Odovzdal projekt iba s funkciou help?",
        "Neprisiel na pisomku/polsemestralku/zapocet kvoli nevolnosti z alkoholu z predoslej noci?",
        "Dostal reakciu od (vazeneho doktora etc.) Fuchsa?",
        "Dostal navrhnute zmenit karieru/skolu od profesora?",
        "Spravil projekt ktory alokoval viac ako terabyte pamate?",
        "Odregistroval si predmet po zaciatku semestra?",
        "Odregistrovali mu povinny predmet kvoli kreditovemu stropu?",
        "Bol 1BIT viac ako raz?",
          ],
      submited: false,
    }
  },
  methods: {
    submit(){
    this.submited = !this.submited
    },
    clear(){
      this.checkedNames = []
    }
  }
}
</script>

<template>
<body >
  <div class="qs" v-if="!submited">

    <ul>
      <li v-for="(name,index) in names">
        <input  type="checkbox" v-model="checkedNames" id={{index}} :value="index" />
        <label for="checkbox"> {{index + 1}}. {{ name }}</label>
      </li>
    </ul>
    <div class="spaced">
    <a  @click="submit" class="button">submit</a>
    <a  @click="clear" class="button">clear</a>
    </div>
  </div>

  <div v-if="submited" class="finale">
    Vas fit purity score: {{names.length-checkedNames.length}}/{{ names.length }}
   </div>
</body>
</template>


<style scoped>
body{
  color: black;
  padding-right: 5;
}
.qs{
  padding-top: 0%;
}
ul{
list-style-type: none;
}
label{
  padding-left: 1%;
}
li input {
  padding: 5px;
}
.finale{
  padding-left: 25%;
  font-size: xx-large;
}
.button {
  display: inline-block;
  background-color: #00aae2;
  color: #ff0027;
  padding: 15px 32px;
  font-size: 16px;
  border-radius: 8px;
}
.button:hover{
  background-color:#ff0027 ;
  color: #00aae2;
  border-radius: 8px;

}
</style>