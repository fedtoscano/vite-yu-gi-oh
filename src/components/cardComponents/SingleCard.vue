<script>
import {store} from "../../store.js";
export default {
data() {
return {
    store
}
}}
</script>

<template>
    <article v-for="card in store.cards" :key="card.id">
        <div class="image-container">
            <img :src="card.card_images[0].image_url" alt="">
        </div>
        <div class="text-container">
            <p>{{ card.name }}</p>
            <p></p>
        </div>
    </article>
</template>

<style scoped lang="scss">
@use "../../style/partials/variables" as *;

article{
    margin-bottom: 1rem;
    background-color: $orange;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: calc((100% / 4) - .5rem);
    .image-container{
            img{
                width: 100%;
                height: 100%;
            }
    }
    .text-container{
        padding: 1rem;
        text-transform: uppercase;
        color: white;
        font-weight: 400;
    }
}
</style>