<template>
    <section class="row">
        <div class="text-uppercase custom-text">you've lived for</div>
        <div class="text-uppercase custom-data">{{ getWeeks }} weeks</div>
        <div class="text-uppercase custom-text">and have about</div>
        <div class="text-uppercase custom-data">{{ getRestWeeks }} weeks</div>
        <div class="text-uppercase custom-text">remaining</div>
        <div class="row">
            <table id="square" class="col-6 col-md-4 mx-auto">
                <tbody>
                    <tr v-for="n in 80" :key="n">
                        <td v-for="n in 52" :key="n"></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </section>
</template>

<script>
export default {
  name: 'Expectancy',
  props: {
    data: Number
  },
  data () {
      return {
          weeks: 0
      }
  },
  computed: {
      getWeeks () {
          return Math.round(this.data / 7)
      },
      getRestWeeks () {
          return  4176 - this.getWeeks 
      },
      getEmptyRow () {
          return Math.floor((this.getRestWeeks - (52 - this.getNotFullRow)) / 52)
      },
  },
  mounted() {
      const td = document.getElementById("square").getElementsByTagName("td");
      for(let i = 0; i < this.getWeeks; i++){
          td[i].classList.add('fullSquare')
      }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
section{
    padding: 90px 0;
    color: white;
    font-size: 3em;
    background: #203040;
}
.custom-data{
    font-size: 1.5em;
}
table{
    border-spacing: 4px;
    border-collapse: separate;
    margin: 0 auto;
}
td{
    border: 1px solid #606989;
    border-radius: 2px;
    font-size: 3px;
    height: 5px;
    width: 5px;
}
.fullSquare{
    background: #606989;
}
</style>