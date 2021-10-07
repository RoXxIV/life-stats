<template>
   <header class="p-5 row">
  <h1 class="text-uppercase">your<span>life</span>stats</h1>
  <p>Enter Your Birthday</p>
  <div id="formDate" class="col-12 col-md-6 mx-auto mt-5">
    <div class="row">
      <div class="col-4">
        <select class="text-uppercase" name="months" id="month" v-model="selectedDate.month">
          <option disabled value="">Month</option>
          <option v-for="month in months" :key="month" :value="month">{{month}}</option>
        </select>
      </div>
      <div class="col-4">
        <select class="text-uppercase" name="days" id="days" v-model="selectedDate.day">
          <option disabled value="">Day</option>
          <option>1</option>
          <option v-for="n in 30" :key="n" :value="n + 1">{{ n + 1 }}</option>
        </select>
      </div>
      <div class="col-4">
        <select class="text-uppercase" name="years" id="years" v-model="selectedDate.year">
          <option disabled value="">Year</option>
          <option v-for="n in ActualYear - offset" :key="n" :value="n+offset">{{ n + offset }}</option>
        </select>
      </div>
      <div class="mt-3">
        <button @click="displayStats" class="btn viewStatsBtn mt-4 text-uppercase">View stats</button>
      </div>
    </div>
  </div>
</header>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      months: ['January','February','March','April','May','June','July','August','September','October','November','December'],
      ActualYear: new Date().getFullYear(),
      offset: 1900,
      allDays: 0,
      selectedDate: {
          day: '',
          month:'',
          year:'',
      }
    }
  },
  computed: {
    getAllDays () {
      const todayDate = new Date().getTime() / 86400000;
      const birthdayDate = new Date(`${this.selectedDate.day} ${this.selectedDate.month} ${this.selectedDate.year}`).getTime() / 86400000;
      console.log(`${this.selectedDate.day} ${this.selectedDate.month} ${this.selectedDate.year}`)
      return Math.floor(todayDate - birthdayDate)
    }
  },
  methods: {
    displayStats () {
        // if all date input are valid , emit data to the parent component as an Obj (payload)
      if (this.selectedDate.day !== '' && this.selectedDate.month !== '' && this.selectedDate.year !== '') {
        this.$emit('getObjDate', { getAllDays: this.getAllDays })
      }
    }
  }
  
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    header{
  background-color: #4B6587;
  color: white;
  background-image: url('../assets/img/mountain1.jpg');
  background-size: cover;
  background-position-y: center;
}
header h1{
  color: #b4b4b4;
}
header h1 span{
  color: white;
}
.viewStatsBtn{
    color: white;
    background: #00bfb0;
    padding: 5px 30px;
  }
  #formDate select{
    padding: 5px;
    background: #F7F6F2;
    border: none;
    /*hide default arrow*/
    -webkit-appearance: none;
    -moz-appearance: none;
    font-size: 17px;
  }
</style>