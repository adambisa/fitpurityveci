<script>
import { compileScript } from "vue/compiler-sfc";

export default {
  data() {
    return {
      checkedNames: [],
      names: [
        "Zaspal na prednaske?",
        "Vynechal skolu na tyzden?",
        "Prisiel az po polovici prednasky?",
        "Odisiel z cvika hned po ziskani bodu?",
        "Submitol zly file projektu?",
        "Odovzdal plagiat?",
        "Zacal projekt (menej) 24 hodin pred odovzdavanim?",
        "Skippol polsemestralku?",
        "Urobil IMA2 skor ako IMA1?",
        "Mal 4 matiky v jednom semestri?",
        "Podal falosnu prekazku v studiu?",
        "Dostal sa do 4BIT+?",
        "Zhodil Merlina/Evu?",
        "Zaregistroval si 2 prekryvajuce sa cvika?",
        "Rozbil pohar v kachne?",
        "Omylom podal OZNUK?",
        "Nadaval na garanta v public chanelli?",
        "Nabural do nejakeho garanta predmetu?",
        "Pohadal sa s vyucujucim?",
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
        "Bol hostom disciplinarnej komisie?",
        "Vychutnal (a) si parky v termoske?",
        "Odovzdal (a) kod s cudzim xloginom?",
        "Neudělal žádný projekt a přesto zvládl předmět?",
        "Pomylil si miestnost na FITe s miestnostou na FEKTe?",
        "Dostal sa na strechu FITu?",
        "Bol obetou incidentu v IMA2?"   
      ],
      engQs: [
        "Fell asleep on a lecture?",
        "Stopped going to school for a week?",
        "Got to the lecture after it was half done?",
        "Left an exercise class right after points were given?",
        "Submitted a bad project file?",
        "Submitted a plagiarized project?",
        "Started to work on a project < 24 hours before the deadline?",
        "Skipped a midterm?",
        "Finished IMA2 before IMA1?",
        "Had 4 math courses in one semester?",
        "Faked absence reason documents?",
        "Got to 3BIT+?",
        "Crashed the Merlin/Eva server(s)?",
        "Registered two exercise classes that are in the same time window?",
        "Broke a glass in Kachna?",
        "Accidentally submitted a study termination request?",
        "Swore at a course guarantor in public channels?",
        "Had an accident with a course guarantor?",
        "Had a conflict with a teacher?",
        "Made the whole D105 laugh?",
        "Had a phone in pocket during an exam?",
        "Got exactly the minimum amount of points for an E?",
        "Completed a course without attending a single lecture?",
        "Submitted a project with only a help function implemented?",
        "Didn't attend a test/exam due to consequences of drinking alcohol the night before?",
        "Got a reaction on a course review from an important doctor or whatever e.g. from Fuchs?",
        "Got a suggestion to change the field of study from a professor?",
        "Made a project that allocates more than a terabyte of memory?",
        "Unregistered a course after the semester started?",
        "Unwillingly had a course unregistered due to credit limits?",
        "Was a 1BIT more than once?",
        "Was summoned to a disciplinary hearing?",
        "Enjoyed sausages from a thermos?",
        "Submitted a file with someone elses xlogin?",
        "Did not do a single project and still managed to pass the class?",
        "Mistook a room at FIT for a room at FEKT?",
        "Stepped foot on the roof of FIT?",
        "Fell victim to an incident in IMA2?"        
      ],
      submited: false,
      eng: false,
      next: this.engQs,
    };
  },
  methods: {
    submit() {
      this.submited = !this.submited;
    },
    clear() {
      this.checkedNames = [];
    },
    switch_lang() {
      console.log(this.eng);
      if (this.eng === false) {
        this.placeholder = this.names;
        this.names = this.engQs;
        this.eng = true;
      } else {
        this.names = this.placeholder;
        this.eng = false;
      }
    },
  },
};
</script>

<template>
  <body>
    <div class="qs" v-if="!submited">
      <ol class="qs__list">
        <li v-for="(name, index) in names">
          <input
            type="checkbox"
            v-model="checkedNames"
            :id="index"
            :value="index"
            :name="name"
          />
          <label :for="index"> {{ name }}</label>
        </li>
      </ol>
      <div class="buttons">
        <a @click="submit" class="button">Submit</a>
        <a @click="clear" class="button">Clear</a>
        <a @click="switch_lang" class="button">switch lang</a>
      </div>
    </div>

    <div v-if="submited" class="finale">
      <div v-if="!eng">
        Vas fit purity score: {{ names.length - checkedNames.length }}/{{
          names.length
        }}
      </div>
      <div v-if="eng">
        Your fit purity score: {{ names.length - checkedNames.length }}/{{
          names.length
        }}
      </div>
      <p>
        Feel free to check out the code. <a href="https://github.com/adambisa/fitpurityveci">here</a>
      </p>
    </div>
  </body>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Gabarito:wght@400;500;600;700&family=Teko:wght@300..700&display=swap");

body {
  color: black;
  padding-right: 5;
}

.qs {
  width: 100%;
}

.qs__list {
  padding-bottom: 1.2rem;
}

label {
  padding-left: 1%;
}

.finale {
  padding-left: 25%;
  font-size: xx-large;
}

.buttons {
  display: flex;
  justify-content: center;
  align-content: center;
  gap: 0.8rem;
  padding-bottom: 2.4rem;
  font-family: "Teko", sans-serif;
}

.button {
  display: inline-block;
  background-color: #00aae2;
  color: white;
  padding: 8px 32px;
  font-size: 1.2rem;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 500;
  letter-spacing: 1px;
}
.button:hover {
  background-color: #ff0027;
  color: #00aae2;
  border-radius: 8px;
}
</style>