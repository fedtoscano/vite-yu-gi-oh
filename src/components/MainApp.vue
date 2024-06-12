<script>
import CardList from "./cardComponents/CardList.vue";
import axios from  "axios";
import {store} from "../store.js"

export default {
components:{
    CardList,
},
data() {
return {  
    store,
    
}
},
methods: {
    getCards: function(){
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0')
            .then((response) => {
                // console.log(response)
                store.cards = response.data.data
                console.log(store.cards);
            })
            .catch(function (error) {
                console.log(error);
            })
            .finally(function () {
                // always executed
            });
    },

},
created(){
        this.getCards()
    },
    }
</script>

<template>
    <div class="container">
        <CardList/>
    </div>
</template>

<style scoped lang="scss">
@use "../style/partials/variables" as *;

.container{
    background-color: $orange;
    padding: 2rem;
}

</style>