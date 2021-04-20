<template>
	<div class="gif" :style="`background-image: url(${gif.images.original.url})`">
		<input ref="url" type="text" :value="gif.images.original.url" />
		<button @click="copyUrl">Copy URL</button>
	</div>
</template>

<script>
export default {
	name: 'Gif',
	data() {
		return {};
	},
	props: ['gif'],
	methods: {
		copyUrl() {
			this.$refs.url.select();
			document.execCommand('copy');
		},
	},
};
</script>

<style scoped>
.gif {
	width: 240px;
	height: 248px;
	background-repeat: no-repeat;
	background-size: cover;
}

.gif input {
	width: 100%;
}

.gif button {
	width: 100px;
	background-color: blanchedalmond;
	border: none;
	border-radius: 5px;
	height: 30px;
}
</style>
