<script setup lang="ts">
import { ref } from "vue";
import SecondaryContainer from "./ui/secondaryContainer.vue";

defineProps<{
	isMetricDropdownOpen: boolean;
}>();

const METRICS = [
	{
		title: "Temperature",
		options: [
			{ label: "Celsius (°C)", value: "celsius", default: true },
			{ label: "Fahrenheit (°F)", value: "fahrenheit", default: false },
		],
	},
	{
		title: "Wind Speed",
		options: [
			{ label: "km/h", value: "kmh", default: true },
			{ label: "mph", value: "mph", default: false },
		],
	},
	{
		title: "Precipitation",
		options: [
			{ label: "Millimeters (mm)", value: "mm", default: true },
			{ label: "Inches (in)", value: "in", default: false },
		],
	},
];

const unitDropdownActive = ref(false);

const selectedTemperatureMetric = ref(METRICS[0]?.options[0]?.value);
const selectedWindSpeedMetric = ref(METRICS[1]?.options[0]?.value);
const selectedPrecipitationMetric = ref(METRICS[2]?.options[0]?.value);

// const renderActiveMetric = (title, metric)
</script>
<template>
	<div class="p-10 flex items-center justify-between">
		<img src="../assets/images/logo.svg" alt="logo" />
		<div class="flex flex-col gap-2 relative items-end">
			<button
				@click="unitDropdownActive = !unitDropdownActive"
				class="flex items-center gap-2 bg-[#252541] px-4 py-2 rounded-lg cursor-pointer w-fit"
			>
				<img src="../assets/images/icon-units.svg" alt="units" />
				<p>Units</p>
				<img src="../assets/images/icon-dropdown.svg" alt="dropdown" />
			</button>
			<SecondaryContainer
				:isDropdownOpen="isMetricDropdownOpen"
				:class="['p-1 absolute top-16 w-max', !unitDropdownActive && 'hidden']"
				:toggle="unitDropdownActive"
			>
				<button
					class="text-white text-md flex flex-row p-2 w-full my-2 rounded-lg items-center justify-between cursor-pointer"
				>
					Switch to Imperial
				</button>
				<ul>
					<li
						v-for="(item, index) in METRICS"
						:key="item.title"
						class="text-gray-400 text-sm py-3"
					>
						{{ item.title }}
						<button
							v-for="metric in item.options"
							:key="metric.value"
							:class="[
								'text-white text-md flex flex-row p-2 w-full my-2 rounded-lg items-center justify-between cursor-pointer hover:bg-[#2f2f49]',
								// metric.default && 'bg-[#2f2f49]',
								(item.title === 'Temperature' &&
									selectedTemperatureMetric === metric.value &&
									'bg-[#2f2f49]') ||
									(item.title === 'Wind Speed' &&
										selectedWindSpeedMetric === metric.value &&
										'bg-[#2f2f49]') ||
									(item.title === 'Precipitation' &&
										selectedPrecipitationMetric === metric.value &&
										'bg-[#2f2f49]'),
							]"
							@click="
								if (item.title === 'Temperature') {
									selectedTemperatureMetric = metric.value;
								} else if (item.title === 'Wind Speed') {
									selectedWindSpeedMetric = metric.value;
								} else {
									selectedPrecipitationMetric = metric.value;
								}
							"
						>
							{{ metric.label }}
							<img
								src="../assets/images/icon-checkmark.svg"
								alt="checkmark"
								:class="{
									hidden:
										(item.title === 'Temperature' &&
											selectedTemperatureMetric !== metric.value) ||
										(item.title === 'Wind Speed' &&
											selectedWindSpeedMetric !== metric.value) ||
										(item.title === 'Precipitation' &&
											selectedPrecipitationMetric !== metric.value),
								}"
							/>
						</button>
						<div
							:class="['w-full h-px bg-gray-600', index === 2 && 'hidden']"
						/>
					</li>
				</ul>
			</SecondaryContainer>
		</div>
	</div>
</template>
