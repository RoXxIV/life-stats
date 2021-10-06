<template>
    <section class="row">
        <div>
            <h2>You have taken <span>{{ data * 20000 }}</span> breaths</h2>
        </div>
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
    padding: 50px 0;
    background: #4B6587;
}
span{
    font-size: 1.3em;
}
</style>