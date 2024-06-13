<script>
import axios from  "axios";
import {store} from "../store.js"

export default {
data() {
return {
    store,
    archetypeList: [],
    selectedArchetype: ""
}
},
methods:{
    getArchetypes: function(){
        axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then((response) => {
            // handle success
            this.archetypeList = response.data
            console.log(this.archetypeList);
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        })
        .finally(function () {
            // always executed
        });
    },

    selectArchetype: function(){
        console.log(this.selectedArchetype)
        // console.log("ciaooo")
    }
},
created(){
    this.getArchetypes()
}}
</script>

<template>
    <div class="container">
        <label for="archetype-selector">Select the Archetype:</label>
        <select name="archetype-selector" id="archetype-selector" v-model="selectedArchetype" @change="selectArchetype">
            <option v-for="(archetype, index) in archetypeList" 
                :key="index" 
                :value="archetype.archetype_name"
                
                >

                {{ archetype.archetype_name }}

            </option>
        </select>
    </div>
</template>

<style scoped>
.container{
    display: flex;
    flex-direction: column;
    align-items: end;
}
</style>