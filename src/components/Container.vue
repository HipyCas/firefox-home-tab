<template>
	<!-- Transparent background or frosted glass effect container is also a good idea, also dark mode of course -->
	<div class="bg-transparent w-screen">
		<div
			class="w-8/12 lg:w-7/12 h-max-content mx-auto py-7 px-7 sm:px-8 md:px-10 lg:px-16 bg-gray-100 z-10 rounded-t-xl"
		>
			<slot></slot>
		</div>
	</div>
</template>

<script>
export default {};
</script>

<style></style>
