<script>
    import ListCards from './ListCards.vue';
    import axios from 'axios';

    export default {
        components : {
            ListCards
        },
        data() {
            return {
                characters: [],
            }
        },      
        methods: {
            getCharacters(){
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                then.(function(response){
                    console.log(response);
                })
                .catch(function(error){
                    console.log(error);
                })
                .finally(function(){
                });
            }
        },
        created () {
            this.getCharacters();
        }
    }
</script>

<template>
    <main>
        <h1>
            ciao
        </h1>
    </main>
    <ListCards/>
</template>

<style lang="scss" scoped>
</style>