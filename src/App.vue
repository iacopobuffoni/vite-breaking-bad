<script>
	import AppHeader from './components/AppHeader.vue';
	import AppMain from './components/AppMain.vue';
	import AppFooter from './components/AppFooter.vue';
	import { store } from './store.js';
	import axios from 'axios';
	export default {
		name: 'App',
  		components : {
			AppHeader,
			AppMain,
			AppFooter

  		},

		data() {

			return {
				store
			}

		},
		methods: {
			getCards() {
				axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php', {
					params: {
						archetype: store.selected
					}
				}).then((response) => {
				this.store.cards = response.data.data;
			});
			}
		},
		created() {
			axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php').then((response) => {
				this.store.cards = response.data.data;
			});
		}
	
	}
</script>

<template>
  	<AppHeader/>
	<AppMain :cardsList="store.cards" :cardsCount="store.cards.length" @search="getCards"/>
	<AppFooter/>
</template>

<style lang="scss">
	@import "styles/main";
</style>
