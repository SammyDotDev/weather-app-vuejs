<script setup lang="ts">
defineProps<{
	size?: string;
	toggle?: boolean;
	isDropdownOpen?: boolean;
}>();
</script>
<template>
	<transition name="fade">
		<div
			v-if="isDropdownOpen ? isDropdownOpen : true"
			class="bg-[#252541] rounded-lg p-2"
		>
			<slot />
		</div>
	</transition>
</template>
<style>
/* Define the duration and timing function of the transition */
.fade-enter-active,
.fade-leave-active {
	transition: opacity 0.5s ease; /* The animation lasts 0.5 seconds */
}

/* Define the starting state for entering and ending state for leaving */
.fade-enter-from,
.fade-leave-to {
	opacity: 0; /* The element starts as invisible when entering and ends as invisible when leaving */
}

/* The 'fade-enter-to' (final enter state) and 'fade-leave-from' (initial leave state) classes are
   automatically applied and have an opacity of 1 by default, so they don't need explicit definition. */
</style>
