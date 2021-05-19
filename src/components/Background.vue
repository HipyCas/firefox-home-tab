<template>
	<div id="bgContainer" class="fixed h-screen w-screen">
		<img :src="pictureURL" alt="" class="object-cover w-full h-full" />
		<a
			class="absolute bottom-0 right-0 px-1 py-0 bg-white bg-opacity-20 text-black hover:underline"
			:href="pictureLink"
		>
			{{ pictureCaption }}
		</a>
		<div
			id="bgCover"
			class="absolute top-0 bg-black bg-opacity-90 w-full h-full"
		></div>
	</div>
</template>

<script>
import { createApi } from 'unsplash-js';
import defaultImage from '../../claudio-carrozzo-4IT1Ch_nebE-unsplash.jpg';

export default {
	props: ['updateBackgroundEvent'],
	data() {
		const unsplash = createApi({
			accessKey: import.meta.env.VITE_UNSPLASH_ACCESS_KEY,
		});

		return {
			unsplash,
			pictureURL: defaultImage,
			pictureCaption: 'HipyCas 2021',
			pictureLink: '#',
		};
	},
	methods: {
		updatePhoto(query = 'nightscape') {
			this.unsplash.photos
				.getRandom({ query })
				.then((result) => {
					if (result.type !== 'success')
						throw new Error(`Unsplash request returned an error: ${result}`);
					this.pictureURL = result.response.urls.full;
					this.pictureCaption = `${result.response.user.name} ${
						result.response.user.updated_at.split('-')[0]
					} - Unsplash`;
					this.pictureLink = result.response.links.html;
					console.info(result.response.user.updated_at);
				})
				.catch((err) => {
					console.log(err);
				});
		},
	},
	mounted() {
		this.updatePhoto();

		window.addEventListener('updateBackground', () => {
			this.updatePhoto();
		});
	},
};
</script>

<style scoped>
#bgContainer {
	z-index: -2;
}
#bgCover {
	z-index: -1;
}
</style>
