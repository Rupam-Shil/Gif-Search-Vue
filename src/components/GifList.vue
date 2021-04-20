<template>
	<div id="giflist">
		<Gif v-for="gif in gifs" :key="gif.id" :gif="gif" />
	</div>
</template>

<script>
import Gif from './Gif';
export default {
	name: 'GifList',
	components: { Gif },
	props: ['gifs'],
};
</script>

<style scoped>
#giflist {
	display: grid;
	grid-gap: 5px;
	grid-template: repeat(3, 1fr) / repeat(3, 1fr);
}
</style>
