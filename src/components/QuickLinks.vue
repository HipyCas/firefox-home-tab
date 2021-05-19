<template>
	<div class="mx-1.5 mb-1 flex justify-between">
		<h2 class="text-lg font-semibold">Quick Links</h2>
		<div>
			<button class="rounded-full h-8 w-8">
				<svg class="fas fa-plus text-black stroke-1"></svg>
			</button>
			<button class="rounded-full h-8 w-8">
				<svg class="fas fa-cog text-black stroke-1"></svg>
			</button>
		</div>
	</div>
	<div class="flex flex-row flex-wrap mx-1.5 mb-2">
		<a
			v-for="link in links"
			:key="link.name"
			class="mr-5 hover:bg-color-gray-300 bg-opacity-20 text-center"
			:href="link.href"
		>
			<div
				class="h-24 w-24 bg-gray-500 rounded-lg flex justify-center items-center"
			>
				<svg class="fab fa-3x" :class="`fa-${link.icon}`" :alt="link.name">
					<des>
						{{ link.name }}
					</des>
				</svg>
			</div>
			<p
				class="font-extralight antialiased text-md text-gray-900 mt-1.5 tracking-wider"
			>
				{{ link.name }}
			</p>
		</a>
	</div>
</template>

<script>
export default {
	// Use fetch(https://fontawesome.com/icons/{link.icon}) and check if status code is different than 200 to see if the icon exists, if not display letter
	data() {
		return {
			links: [
				{
					href: 'https://github.com/',
					name: 'GitHub',
					icon: 'github',
				},
				{
					href: 'https://wakatime.com/',
					name: 'Wakatime',
					icon: 'wakatime',
				},
			],
		};
	},
};
</script>

<style></style>
