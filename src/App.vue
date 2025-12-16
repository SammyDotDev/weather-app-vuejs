<script setup lang="ts">
import { ref } from "vue";
import Nav from "./components/Nav.vue";

const isMetricDropdownOpen = ref(false);
</script>

<template>
	<div
		v-if="isMetricDropdownOpen"
		class="fixed inset-0 z-10"
		@click="isMetricDropdownOpen = false"
	></div>
	<div class="">
		<Nav isMetricDropdownOpen="isMetricDropdownOpen"/>
	</div>
</template>

<style scoped>
.logo {
	height: 6em;
	padding: 1.5em;
	will-change: filter;
	transition: filter 300ms;
}
.logo:hover {
	filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
	filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
