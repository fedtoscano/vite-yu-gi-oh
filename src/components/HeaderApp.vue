<script>
export default {
data() {
return {  
}
}}
</script>

<template>
    <div class="container">
        <div class="img-container">
            <img src="../assets/yugioh-logo.png" alt="YuGiOh main logo">
        </div>
        <h2>Yu-Gi-Oh API</h2>
    </div>
</template>

<style scoped lang="scss">
.container{
    display: flex;
    align-items: center;

    .img-container{
        width: 100px;
        margin-right: 2em;

        img{
            width: 100%;
        }
    }
}
</style>