<template>
    <section class="row">
        <div>
            <h2>You are <span>{{ data }}</span> days old</h2>
        </div>
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
    background: #F7F6F2;
    padding: 50px 0;
    color: #4B6587;
}
span{
    font-size: 1.3em;
}
</style>