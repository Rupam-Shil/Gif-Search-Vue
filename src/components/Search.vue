<template>
	<div id="cover">
		<form>
			<div class="tb">
				<div class="td">
					<input
						type="text"
						placeholder="Search"
						v-model="keyword"
						@input="onInput"
					/>
				</div>
			</div>
		</form>
	</div>
</template>

<script>
import env from '../env';
export default {
	name: 'Search',
	data() {
		return {
			keyword: '',
			timeOut: null,
			gifs: {},
		};
	},
	methods: {
		onInput() {
			clearTimeout(this.timeOut);
			this.timeOut = setTimeout(() => {
				this.search();
			}, 500);
		},
		search() {
			if (this.keyword != '') {
				fetch(
					`https://api.giphy.com/v1/gifs/search?api_key=${env.apikey}&q=${this.keyword}&limit=9`
				)
					.then((res) => res.json())
					.then((data) => {
						this.gifs = data.data;
						this.$emit('gifs', this.gifs);
					});
			}
		},
	},
};
</script>

<style scoped>
.tb {
	display: table;
	width: 100%;
}

.td {
	display: table-cell;
	vertical-align: middle;
}

input {
	color: #fff;
	font-family: Nunito;
	padding: 0;
	margin: 0;
	border: 0;
	background-color: transparent;
}

#cover {
	position: absolute;
	top: 80px;
	left: 0;
	right: 0;
	width: 100%;
	padding: 35px;
	margin: -83px auto 0 auto;
	background-color: #ff7575;
	border-radius: 20px;
	box-shadow: 0 10px 40px #ff7c7c, 0 0 0 20px #ffffffeb;
	transform: scale(0.6);
}

form {
	height: 96px;
}

input[type='text'] {
	width: 100%;
	height: 96px;
	font-size: 60px;
	line-height: 1;
}

input[type='text']::placeholder {
	color: #fff;
}
</style>
