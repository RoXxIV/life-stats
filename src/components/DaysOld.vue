<template>
    <section class="row">
        <div class="text-uppercase">You are </div>
        <div class="text-uppercase">{{ data.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',') }}</div>
        <div class="text-uppercase">days old</div>
    </section>
</template>

<script>
export default {
  name: 'DaysOld',
  props: {
    data: Number
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
section{
    padding: 90px 0;
    color: white;
    font-size: 3em;
}
</style>