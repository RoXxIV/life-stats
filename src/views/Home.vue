<template>
<header class="p-5 row">
  <h1>Life stats</h1>
  <div id="formDate" class="col-12 col-md-6 mx-auto mt-5">
    <div class="row">
      <div class="col">
        <select name="months" id="month" v-model="selectedMonth">
          <option disabled value="">Month</option>
          <option v-for="month in months" :key="month" :value="month">{{month}}</option>
        </select>
      </div>
      <div class="col">
        <select name="days" id="days" v-model="selectedDay">
          <option disabled value="">Day</option>
          <option>1</option>
          <option v-for="n in 30" :key="n" :value="n + 1">{{ n + 1 }}</option>
        </select>
      </div>
      <div class="col">
        <select name="years" id="years" v-model="selectedYear">
          <option disabled value="">Year</option>
          <option v-for="n in ActualYear - offset" :key="n" :value="n+offset">{{ n + offset }}</option>
        </select>
      </div>
      <div class="mt-3">
        <button @click="displayStats" class="btn viewStatsBtn mt-4">View stats</button>
      </div>
    </div>
  </div>
</header>
<main v-if="showStats">
  <DaysOld :data="getAllDays" />
  <BreathsTaken :data="getAllDays" />
</main>
</template>

<script>
// @ is an alias to /src
import DaysOld from '../components/DaysOld.vue'
import BreathsTaken from '../components/BreathsTaken.vue'
export default {
  name: 'Home',
  components: {
    DaysOld,
    BreathsTaken
  },
  data () {
    return {
      months: ['January','February','March','April','May','June','July','August','September','October','November','December'],
      ActualYear: new Date().getFullYear(),
      offset: 1900,
      selectedDay: '',
      selectedMonth:'',
      selectedYear:'',
      allDays: 0,
      showStats: false

    }
  },
  computed: {
    getAllDays () {
      const todayDate = new Date().getTime() / 86400000;
      const birthdayDate = new Date(`${this.selectedDay} ${this.selectedMonth} ${this.selectedYear}`).getTime() / 86400000;
      console.log(`${this.selectedDay} ${this.selectedMonth} ${this.selectedYear}`)
      return Math.floor(todayDate - birthdayDate)
    }
  },
  methods: {
    displayStats () {
      if (this.selectedDay !== '' && this.selectedMonth !== '' && this.selectedYear !== '') {
        return this.showStats = true;
      }
      console.log(this.getAllDays)
    }
  }
}
</script>
<style>
header{
  margin: auto;
  text-transform: uppercase;
  background-color: #4B6587;
  color: white;
}
.viewStatsBtn{
    color: #4B6587;
    background: #F7F6F2;
    font-weight: bold;
  }
  #formDate select{
    padding: 5px;
    font-size: 1.5em;
    color: #4B6587;
    background: #F7F6F2;
    border: none;
    /*hide default arrow*/
    -webkit-appearance: none;
    -moz-appearance: none;
    text-align: center;
  }
</style>
