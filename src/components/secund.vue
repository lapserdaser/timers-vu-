<template>
	<div id="secund">
		<p :class="{ 'active': !isHidden }">{{ formattedElapsedTime }}</p>
		<span :class="{ 'active': !isHidden }"> </span>
		<div div class=" btns">
			<button v-on:click="isHidden = !isHidden" v-show="isHidden" @click="start"><svg width="17" height="20"
					viewBox="0 0 17 20" fill="none" xmlns="http://www.w3.org/2000/svg">
					<path :class="{ 'active': !isHidden }" d="M0 20V0L17 10L0 20Z" fill="#9E9E9E" />
				</svg>
			</button>
			<button v-on:click="isHidden = !isHidden" v-show="!isHidden" @click="stop"><svg width="10" height="20"
					viewBox="0 0 10 20" fill="none" xmlns="http://www.w3.org/2000/svg">
					<rect :class="{ 'active': !isHidden }" x="7" width="3" height="20" fill="#9E9E9E" />
					<rect :class="{ 'active': !isHidden }" width="3" height="20" fill="#9E9E9E" />
				</svg>
			</button>
			<button v-on:click="isHidden = true" @click="reset"><svg width="20" height="20" viewBox="0 0 20 20" fill="none"
					xmlns="http://www.w3.org/2000/svg">
					<rect :class="{ 'active': !isHidden }" width="20" height="20" fill="#9E9E9E" />
				</svg>
			</button>
		</div>

	</div>
</template>

<script>
export default {
	name: "MySecund",
	data() {
		return {
			elapsedTime: 0,
			timer: undefined,
			isHidden: true,
		};
	},
	computed: {
		formattedElapsedTime() {
			let date = new Date(null);
			date.setSeconds(this.elapsedTime / 1000);
			//const utc = date.toUTCString();
			//return utc.substr(utc.indexOf(":") - 2, 8);
			let h = date.getHours() - 3;
			let m = date.getMinutes().toString().padStart(2, 0);
			let s = date.getSeconds().toString().padStart(2, 0);
			if (date > 3599000) {
				return h.toString().padStart(2, 0) + ':' + m + ':' + s;
			} else if (date > 59000) {
				return m + ':' + s;
			}
			else {
				return s;
			}

		}
	},
	methods: {
		start() {
			this.timer = setInterval(() => {
				this.elapsedTime += 1000;
			}, 1000);
		},
		stop() {
			clearInterval(this.timer);
		},
		reset() {
			clearInterval(this.timer);
			this.elapsedTime = 0;
		},
	}
};
</script>