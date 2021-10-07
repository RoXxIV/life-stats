<template>
<Header @getObjDate="getData" />
<main v-if="getAllDays !== ''">
  <DaysOld :data="getAllDays" />
  <Expectancy :data="getAllDays" />
  <BreathsTaken :data="getAllDays" />
</main>
</template>

<script>
// @ is an alias to /src
import Header from '../components/Header.vue'
import DaysOld from '../components/DaysOld.vue'
import BreathsTaken from '../components/BreathsTaken.vue'
import Expectancy from '../components/Expectancy.vue'
export default {
  name: 'Home',
  components: {
    Header,
    DaysOld,
    BreathsTaken,
    Expectancy,
  },
  data () {
    return {
      getAllDays: ''
    }
  },
  methods: {
    getData(payload) {
      // get all days from child 
      this.getAllDays = payload.getAllDays
    }
  }
}
</script>
<style>

</style>
