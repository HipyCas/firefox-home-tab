<template>
	<!-- FIXED -->
	<!-- Fixed background image from Unsplash -->
	<Background :updateBackgroundEvent="updateBackgroundEvent" />
	<!-- Search? and icons with config and other stuff -->
	<Toolbar :updateBackgroundEvent="updateBackgroundEvent" />

	<!-- CONTENT -->
	<!-- Header with a welcoming message and maybe quotes or time -->
	<Header />
	<Container>
		<QuickLinks />
		<!-- Maybe move to header? -->
		<Weather />
		<!-- Infinite scroll? news -->
		<News />
	</Container>
</template>

<script setup>
import Background from './components/Background.vue';
import Toolbar from './components/Toolbar.vue';

import Header from './components/Header.vue';
import Container from './components/Container.vue';

import QuickLinks from './components/QuickLinks.vue';
import News from './components/News.vue';

const updateBackgroundEvent = new Event('updateBackground', {
	bubbles: true,
	cancelable: true,
	composed: true,
});

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #2c3e50;
}
</style>
