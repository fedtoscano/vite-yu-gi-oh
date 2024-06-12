<script>
import CardList from "./cardComponents/CardList.vue";
import axios from  "axios";
import store from "../store.js"

export default {
components:{
    CardList,
},
data() {
return {  
}
},
methods: {
    getCards: function(){
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0')
            .then((response) => {
                // handle success
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
        <h1>ciao dal main App</h1>
        <CardList/>

    </div>
</template>

<style scoped lang="scss">
@use "../style/partials/variables" as *;

.container{
    background-color: $orange;
}

</style>