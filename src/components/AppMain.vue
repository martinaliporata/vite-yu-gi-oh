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
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0')
                .then((response) => {
                    console.log(response.data.data);
                    this.characters=response.data.data;
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
            console.log(this.getCharacters)
        }
    }
</script>

<template>
    <main> 
        <label for="choice">Choose according to the archetype</label>
        <select name="archetype" id="archetype">
            <option v-for="" value=""></option>
        </select>
        <!-- lo passo via props a listcards -->
        <ListCards :characters="this.characters"/>
    </main>
</template>

<style lang="scss">
    @use '../node_modules/bootstrap/scss/bootstrap.scss';
    @use '../style/partials/variabili' as *;

    main {
        background-color: $orange;
    }
</style>