<script>
import CardList from "./cardComponents/CardList.vue";

export default {
components:{
    CardList,
},
data() {
return {  
}
}}
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