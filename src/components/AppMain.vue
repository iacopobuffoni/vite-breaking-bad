<script>
export default {
    name: 'AppMain',
    props: {
        cardsList: {
            type: Array,
            deafult: []
        },
        cardsCount: {
            type: Number,
            default: 0
        }
    }
}
</script>

<template>
    <main>
        <form action="">
            <select name="type" id="" class="ms-5 mt-3">
                <option value="alien"> Alien </option>
            </select>
        </form>
        <div class="container p-5">
            <div class="row">
                <p> Found {{ cardsCount }} cards </p>
            </div>
            <div class="row row-cols-lg-5">
                <div class="col text-center mb-5" v-for="cards in cardsList">
                    <div>
                        <img :src="`${cards.card_images[0].image_url}`" alt="" class="img-fluid">
                    </div>
                    <h4 class="mt-2">
                        {{ cards.name }}
                    </h4>
                    <h6 class="mt-2"> {{ cards.archetype }} </h6>
                </div>
            </div>
        </div>
    </main>
</template>

<style lang="scss" scoped>
@import "../styles/appmain";
</style>