<script>
    import SingleCard from './SingleCard.vue'
    export default {
        data() {
            return {
            }
        },
        components : {
            SingleCard
        },
        props:{
            characters: {
                type: Array,
                required: true
            }
        }
    }
</script>

<template>
    <section class="characters-container">
        <div class="row">
            <h2 class="col-12">
                Main section
            </h2>
            <div class="col-12">
                <div class="row">
                    <article v-for="character in characters" :key="index" class="col-3">
                        <div class="card w-100">
                            <img :src="character.card_images.0.image_url" alt="">
                            <h4>
                                {{character.name }}
                            </h4>
                            <p>
                                {{character.archetype }}
                            </p>
                        </div>
                    </article>
                </div>
            </div>
        </div>
    </section>
    <SingleCard/>
</template>

<style lang="scss" scoped>
</style>