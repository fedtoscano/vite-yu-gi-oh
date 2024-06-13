<script>
import CardList from "./cardComponents/CardList.vue";
import MainSelect from "./MainSelect.vue";
import axios from  "axios";
import {store} from "../store.js"

export default {
components:{
    CardList,
    MainSelect,

},
data() {
return {  
    store,
    isLoaded: false,
    
}
},
methods: {
    getCards: function(){
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0')
            .then((response) => {
                store.cards = response.data.data
            })
            .catch(function (error) {
                console.log(error);
            })
    },
    delayLoading: function(){
        setTimeout(()=>{
            this.getCards(),
            this.isLoaded=true
        },3000)
    },
    researchByArchetype: function(archetype){
        console.log(archetype)
        // ! perché non funziona la chiamata api?
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php', {
            params: {
            archetype: archetype
            }
        })
        .then((response) => {
            store.cards = response.data.data
            console.log(response);
            console.log(store.cards)
        })
        .catch(error => {
            console.log(error)
        })
        .finally(function () {
            // always executed
        });  
    }

},
created(){
        this.getCards(),
        this.delayLoading()
    },
    }
</script>

<template>
    <div class="container" v-if="isLoaded">
        <MainSelect @gotArchetype="researchByArchetype"/>
        <CardList/>
    </div>
    <div class="loader-container" v-else>
        <span class="loader"></span>
    </div>
</template>

<style scoped lang="scss">
@use "../style/partials/variables" as *;

.container{
    background-color: $orange;
    padding: 2rem;
}
.loader-container{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
.loader {
    width: 48px;
    height: 48px;
    border: 3px solid #FFF;
    border-radius: 50%;
    display: inline-block;
    position: relative;
    box-sizing: border-box;
    animation: rotation 1s linear infinite;
    }
    .loader::after {
    content: '';  
    box-sizing: border-box;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 56px;
    height: 56px;
    border-radius: 50%;
    border: 3px solid;
    border-color: #FF3D00 transparent;
    }

    @keyframes rotation {
    0% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(360deg);
    }
} 

</style>