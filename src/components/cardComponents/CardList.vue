<script>
import SingleCard from "./SingleCard.vue";
import {store} from "../../store.js"

export default {
components:{
    SingleCard
},
data() {
return {
    store
}
}}
</script>

<template>
    <h1>ciao da CardList</h1>
    <div class="container">

        <SingleCard/>
    </div>
</template>

<style scoped lang="scss">
.container{
    background-color: white;
    max-width: 1200px;
    margin: 0 auto;
}
</style>