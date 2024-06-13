<script>
import {store} from "../../store.js";
export default {
    props:{
        cardName: String,
        cardImage: String,
        cardArchetype: String,
    },
data() {
return {
    store
}
}}
</script>

<template>
    <article>
        <div class="image-container">
            <img :src="cardImage" alt="">
        </div>
        <div class="text-container">
            <p>{{ cardName }}</p>
            <p>{{ cardArchetype }}</p>
        </div>
    </article>
</template>

<style scoped lang="scss">
@use "../../style/partials/variables" as *;

article{
    border: 1px solid white;
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
        text-align: center;
        padding: 1rem;
        text-transform: uppercase;
        color: white;
        font-weight: 400;
        p{
            margin-bottom: .5em;
        }
    }
}
</style>