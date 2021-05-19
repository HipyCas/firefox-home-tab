<template>
	<div class="fixed top-0 left-0 flex">
		<!-- Settings -->
		<button
			class="bg-black rounded-full w-8 h-8"
			@click="settingsOpen = !settingsOpen"
		>
			<svg class="fas fa-cog text-white"></svg>
		</button>
		<div
			v-if="settingsOpen"
			class="absolute top-9 left-0.5 bg-black rounded-lg px-3 py-2.5 w-72 z-30"
		>
			<div class="relative w-full h-full">
				<button @click="settingsOpen = false" class="absolute -top-1 right-0">
					<svg class="fas fa-times text-white"></svg>
				</button>
				<div class="w-full h-full flex-col justify-items-start text-left">
					<h5 class="text-md text-white font-semibold">Background</h5>
					<div>
						<label
							for="image-query-input"
							class="w-full block text-left text-gray-200 text-xs antialiased mb-1"
							>Unsplash image search query</label
						>
						<input
							id="image-query-input"
							@change="updateBackground()"
							type="text"
							placeholder="nightscape"
							class="block bg-gray-700 bg-opacity-20 p-1 rounded-lg w-56 placeholder-gray-700 text-gray-400"
						/>
					</div>
					<h5 class="text-md text-white font-semibold">Theme</h5>
					<div>
						<input name="theme" type="radio" value="light" /><label for="light"
							>Light</label
						>
						<input name="theme" type="radio" checked value="dark" /><label
							for="dark"
							>Dark</label
						>
					</div>
				</div>
			</div>
		</div>
		<!-- Refresh background -->
		<button
			@click="updateBackground()"
			id="refresh-button"
			class="bg-black rounded-full w-8 h-8"
		>
			<svg class="fas fa-sync-alt text-white"></svg>
		</button>
		<!-- Search -->
		<button
			@click="searchOpen = true"
			v-if="!searchOpen"
			class="bg-black rounded-full w-8 h-8"
		>
			<svg class="fas fa-search text-white"></svg>
		</button>
		<form
			class="bg-black rounded-full min-w-max h-8 px-2"
			v-if="searchOpen"
			method="GET"
			:action="`https://duckduckgo.com/?q=${searchQuery}`"
		>
			<input
				type="search"
				placeholder="Search with DuckDuckGo..."
				class="w-max placeholder-gray-400 text-sm text-white bg-transparent"
				v-model="searchQuery"
			/>
			<button @click="searchOpen = false" class="inline">
				<svg class="fas fa-times text-white"></svg>
			</button>
		</form>
	</div>
</template>

<script>
export default {
	props: ['updateBackgroundEvent'],
	data() {
		return {
			searchOpen: false,
			searchQuery: '',
			settingsOpen: false,
		};
	},
	methods: {
		updateBackground() {
			window.dispatchEvent(this.updateBackgroundEvent);
		},
	},
	setup() {},
};
</script>

<!--style scoped>
#refresh-button:hover {
	@apply fa-spin;
}
</!--style-->
