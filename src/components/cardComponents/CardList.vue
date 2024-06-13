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
    <div class="container">
        <!-- !modificare con v-for (tramite props a SingleCard) -->
        <SingleCard v-for="card in store.cards"
            :cardId="card.id"
            :cardName="card.name" 
            :cardImage="card.card_images[0].image_url"
            :cardArchetype="card.archetype" />
    </div>
</template>

<style scoped lang="scss">
.container{
    display: flex;
    gap: .5rem;
    flex-wrap: wrap;
    background-color: white;
    max-width: 1200px;
    margin: 0 auto;
}
</style>