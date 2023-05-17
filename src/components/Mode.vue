<script setup lang="ts">
	import { ref } from 'vue';

	let darkMode = ref(true)
</script>

<template>
	<div id="mode" @click="darkMode = !darkMode">
		<Transition>
			<img id="sun" v-show="!darkMode" />
		</Transition>
		<Transition :css="false">
			<img id="sun-bg" v-show="!darkMode" />
		</Transition>
		<Transition>
			<img id="moon" v-show="darkMode" />
		</Transition>
		<Transition :css="false">
			<img id="moon-bg" v-show="darkMode" />
		</Transition>
	</div>
</template>

<style scoped>
#mode {
	cursor: pointer;
	position: fixed;
	width: 30px;
	height: 30px;
	top: 20px;
	right: 20px;
}

#sun, #moon {
	position: absolute;
	top: 0px;
	right: 0px;
	width: 30px;
	height: 30px;
}

#sun-bg, #moon-bg {
	position: absolute;
	top: -8px;
	right: -8px;
	width: 46px;
	height: 46px;
	z-index: -1;
	animation: spin 25s linear infinite;
	opacity: 0.75;
}

#sun {
	content: url('../assets/sun_ico.png');
}

#sun-bg {
	content: url('../assets/sun_flare.png');
}

#moon {
	content: url('../assets/moon_ico.png');
}

#moon-bg {
	content: url('../assets/moon_flare.png');
}

@keyframes spin {
	0% {
		opacity: 0;
	}
	5% {
		opacity: 1;
	}
	25% { 
		transform: rotate(90deg);
		filter: brightness(1.2);
	}
	50% { 
		transform: rotate(180deg);
		filter: brightness(0.7);
	}
	75% { 
		transform: rotate(270deg);
		filter: brightness(1.45);
	}
	95% {
		opacity: 1;
	}
	100% { 
		transform: rotate(360deg);
		filter: brightness(1.8);
		opacity: 0;
	}
}

.v-enter-active,
.v-leave-active {
  transition: opacity 1s ease;
}

.v-enter-from,
.v-leave-to {
	opacity: 0;
}
</style>
