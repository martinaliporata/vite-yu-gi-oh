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
                archetypes: [],
                selectedArchetype: '',
            }
        },      
        methods: {
            getCharacters(){
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0')
                .then((response) => {
                    this.characters=response.data.data;
                })
                .catch(function(error){
                    console.log(error);
                })
                .finally(function(){
                });
            },
            getArchetypes(){
                axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
                .then((response) => {
                    this.archetypes=response.data;
                })
                .catch(function(error){
                    console.log(error);
                })
                .finally(function(){
                });
            },
            handleChange (event) {
                console.log(event)
                this.selectedArchetype=event.target.value;
                // event.target.value è valore che seleziona utente nella select
                axios.get(this.selectedArchetype===''?'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0': `https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${this.selectedArchetype}`)
                .then((response) => {
                    this.characters=response.data.data;
                    console.log('gaurda',response)
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
            this.getArchetypes();
        }
    }
</script>

<template>
    <main>
        <label for="choice">Choose according to the archetype</label>
        <select name="archetype" id="archetype" v-model="selectedArchetype" @change="handleChange">
            <option value="">
                All values
            </option>
            <option v-for="(archetype,index) in archetypes" :key="index" :value="archetype.archetype_name">
                {{ archetype.archetype_name }}
            </option>
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