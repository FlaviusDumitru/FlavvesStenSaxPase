<script setup>
const props = defineProps(['userAlternative', 'computerAlternative', 'winnerInfo'])

</script>

<template>
  <!--Kort för att visa vad varje spelare valde-->
  <div v-if="props.winnerInfo!==''" id="vemVann">
    <p>Du valde {{props.userAlternative}}</p>
    <p>Jag valde {{props.computerAlternative}}</p>
    <p>{{ props.winnerInfo }}</p>
  </div>
</template>

<style scoped>
#vemVann {
  margin:auto;
  width:100%;
  background-color: rgba(255, 187, 0, 0.778);

}
</style>