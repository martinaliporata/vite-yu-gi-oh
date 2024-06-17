<script>
    import ListCards from './ListCards.vue';
    import axios from 'axios';

    export default {
        components : {
            ListCards
        },
        data() {
            return {
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