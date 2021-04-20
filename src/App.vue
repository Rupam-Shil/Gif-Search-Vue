<template>
	<div><Search @gifs="addGifs" /> <GifList :gifs="gifs" /></div>
</template>

<script>
import Search from './components/Search';
import GifList from './components/GifList';

export default {
	name: 'App',
	data() {
		return {
			gifs: [],
		};
	},
	components: { Search, GifList },
	methods: {
		addGifs(com) {
			this.gifs = com;
		},
	},
};
</script>

<style>
* {
	box-sizing: border-box;
}
body {
	background: rgb(255, 223, 225);
	padding-top: 150px;
	background: radial-gradient(
		circle,
		rgba(255, 223, 225, 1) 43%,
		rgba(255, 117, 117, 1) 95%
	);
}
</style>
