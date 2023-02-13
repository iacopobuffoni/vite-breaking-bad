<script>
import { store } from '../store.js';
export default {
    name: 'AppMain',
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <main>
        <form action="">
            <select v-model="store.selected" name="archetype" id="" class="ms-5 mt-3">
                <option selected value=""> Select Archetype </option>
                <option value="d/d" @click="$emit('search')"> D/D </option>
                <option value="gem-" @click="$emit('search')"> Gem- </option>
                <option value="cipher" @click="$emit('search')"> Cipher </option>
                <option value="dark magician" @click="$emit('search')"> Dark Magician </option>
                <option value="laval" @click="$emit('search')"> Laval </option>
                <option value="performapal" @click="$emit('search')"> Performapal </option>
                <option value="vylon" @click="$emit('search')"> Vylon </option>
            </select>
        </form>
        <div class="container p-5">
            <div class="row">
                <p> Found {{ store.cards.length }} cards </p>
            </div>
            <div class="row row-cols-lg-5">
                <div class="col text-center mb-5" v-for="cards in store.cards">
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