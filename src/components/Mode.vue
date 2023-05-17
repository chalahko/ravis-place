<script setup lang="ts">
	import { ref } from 'vue';

	let darkMode = ref(true)
</script>

<template>
	<div id="mode" @click="darkMode = !darkMode">
		<Transition>
			<img id="sun" v-if="!darkMode"/>
		</Transition>
		<Transition>
			<img id="sun-bg" v-if="!darkMode"/>
		</Transition>
		<Transition>
			<img id="moon" v-if="darkMode"/>
		</Transition>
		<Transition>
			<img id="moon-bg" v-if="darkMode"/>
		</Transition>
	</div>
</template>

<style scoped>
#mode {
	cursor: pointer;
	position: fixed;
	width: 36px;
	height: 36px;
	top: 20px;
	right: 20px;
}

#sun, #moon {
	position: absolute;
	top: 0px;
	right: 0px;
	width: 36px;
	height: 36px;
}

#sun {
	content: url('../assets/sun_ico.png');
}

#sun-bg, #moon-bg {
	position: absolute;
	top: -8px;
	right: -8px;
	width: 52px;
	height: 52px;
	z-index: -1;
	animation: spin 10s linear infinite;
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
	100% { 
		transform: rotate(360deg);
		filter: brightness(1);
	}
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.75s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
