<template>
	<div id="app">
		<div class="container">

			<MySecund v-for="index in count" :key="index" />

			<div class="btn">
				<button v-on:click="addSecond">
					<p>+</p>
				</button>
			</div>
		</div>
	</div>
</template>

<script>
import MySecund from './components/secund.vue'

export default {
	name: 'App',
	components: {
		MySecund,
	},
	data() {
		return {
			count: 1
		};
	},
	methods: {
		addSecond() {
			this.count += 1;
		}
	}

}
</script>

<style>
* {
	margin: 0;
	padding: 0;
	transition: all 0.2s;
}

button {
	padding: 0;
	border: none;
	font: inherit;
	color: inherit;
	background-color: transparent;
}

@font-face {
	font-family: "gothampro";
	src: local("gothampro"), url(./fonts/gothampro_medium.ttf);
}

#app {
	text-align: center;
	color: #9E9E9E;
	font-family: "gothampro";
}

body {
	background-color: #353638;
}

#secund {
	position: relative;
	background-color: #696969;
	width: 225px;
	height: 120px;
}

span {
	content: "";
	display: block;
	position: absolute;
	top: 60px;
	width: 223px;
	border: 1px solid #9E9E9E;
}

#secund p {
	line-height: 60px;

}

.container {
	margin: 40px auto;
	padding: 0 135px;
	max-width: 775px;
	min-width: 500px;
	display: grid;
	justify-content: center;
	align-content: center;


	grid-template-columns: repeat(3, 225px);
	grid-template-rows: repeat(3, 120px);
	gap: 45px 50px;
}

.btns {
	height: 40px;
	padding-top: 20px;
}

.btns button {
	width: 20px;
	margin: 0 24px;
	cursor: pointer;
}

.btns button:hover {
	scale: 1.2;
}

.btn {
	width: 225px;
}

.btn button {
	font-size: 40px;
	font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
	font-weight: 200;
	background-color: #696969;
	width: 225px;
	height: 120px;
	cursor: pointer;
}

.btn button:hover p {
	scale: 1.1;
	color: #fff;
}

.active {
	fill: #fff;
	color: #fff;
	border-color: #fff;
}

@media (max-width: 1024px) {
	.container {

		display: grid;
		grid-template-columns: repeat(2, 225px);
		grid-template-rows: repeat(2, 120px);
		gap: 45px 50px;
	}
}

@media (max-width: 768px) {
	.container {

		display: grid;
		grid-template-columns: repeat(1, 225px);
		grid-template-rows: repeat(1, 120px);
		gap: 45px 50px;
	}
}
</style>
