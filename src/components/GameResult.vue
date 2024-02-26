<script setup>
import {watch, defineProps, ref } from 'vue';

const prop = defineProps(['result'])
const userScore=ref(0)
const computerScore=ref(0)


// Bevaka när props har ändrats
watch(prop, () => {
   if ( prop.result.winner === 'user'){
    userScore.value++
   } else if (prop.result.winner === 'computer') {
    computerScore.value++
   }
})
</script>

<template>
    <div v-if="userScore || computerScore">
        <span id="userScore">
            <span :class="userScore > computerScore ? 'leader score' : 'score'">{{ userScore }}</span>
            <p v-if="computerScore > userScore">Loser</p>
            <p v-else>User</p>
        </span>
        <span id="computerScore">
            <span :class="userScore < computerScore ? 'leader score' : 'score'">{{ computerScore }}</span>
        <p>Computer</p>
        </span>
    </div>
</template>

<style scoped>
    div {
    margin:auto;
    padding:0.5em;
    width:50%;
    display:flex;
    justify-content: center;
    }

    .score {
        background-color: rgb(6, 109, 74);
        font-size:3em;
        width:3em;
        height:3em;
        display: inline-block;
        text-align: center;
        margin:0.2em;
    }

.leader {
    color:wheat;
    font-size:5em;

}

    p {
        text-align: center;
    }
</style>