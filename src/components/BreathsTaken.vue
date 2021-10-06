<template>
    <section class="row">
        <div class="text-uppercase breathText">You have taken</div>
        <div class="text-uppercase dataBreath">{{ (data * 20000).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',') }} breaths</div>
    </section>
</template>

<script>
export default {
  name: 'BreathsTaken',
  props: {
    data: Number
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
section{
    color: #F7F6F2;
    padding: 90px 0;
    background: #203040;
}
.breathText{
    font-size: 3em;
}
.dataBreath{
   font-size: 2em; 
}
</style>