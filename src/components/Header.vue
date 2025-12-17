<template>
	<div class="flex flex-col items-center justify-center gap-6">
		<h1 class="text-[50px]">How's the sky looking today?</h1>
		<div class="flex items-center justify-center gap-3">
			<div class="px-5 flex items-center gap-2 bg-[#2f2f49] rounded-xl w-[500px]">
				<img src="../assets/images/icon-search.svg" alt="" />
				<input
					type="search"
					placeholder="Search for a place..."
					name="place"
					id="place"
					class="w-full px-4 py-4 text-white bg-[#2f2f49] rounded-xl outline-0 text-lg"
				/>
			</div>
			<div class="bg-[#4657d9] rounded-xl p-[2px]">
				<button
					class="px-4 py-3 text-white rounded-xl bg-[#4657d9] border-[3px] border-black text-lg"
				>
					Search
				</button>
			</div>
		</div>
	</div>
</template>
