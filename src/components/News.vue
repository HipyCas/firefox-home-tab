<template>
	<div class="mx-1.5 pt-1 flex justify-between">
		<h2 class="text-lg font-semibold">News</h2>
		<div>
			<button class="rounded-full h-8 w-8">
				<svg class="fas fa-cog text-black stroke-1"></svg>
			</button>
		</div>
	</div>
	<div class="grid grid-cols-2">
		<p
			v-if="news.length < 1"
			class="col-span-2 text-center text-lg animate-pulse"
		>
			Loading...
		</p>
		<article
			v-for="article in news"
			:key="article.url"
			v-if="news.length > 1"
			class="m-1.5 p-1.5 border rounded hover:bg-white hover:shadow group"
			@click="open(article)"
		>
			<div class="rounded h-28 overflow-hidden">
				<img :src="article.urlToImage" class="object-cover object-center" />
			</div>
			<a
				:href="article.url"
				class="whitespace-normal w-full text-left font-bold text-md hover:text-blue-600 group-hover:text-blue-600"
				>{{ article.title }}</a
			>
			<p class="text-left text-xs text-gray-400">{{ article.author }}</p>
			<p class="text-justify text-sm">{{ article.content }}</p>
		</article>
	</div>
</template>

<script>
export default {
	data() {
		return {
			query: 'science',
			news: [],
		};
	},
	methods: {
		open(article) {
			window.location.href = article.url;
		},
	},
	mounted() {
		fetch(
			`https://cors-anywhere.herokuapp.com/https://newsapi.org/v2/top-headlines?country=${'us'}&apiKey=${
				import.meta.env.VITE_NEWS_API_KEY
			}`,
			{
				mode: 'cors',
			}
		)
			.then((response) => response.json())
			.then((data) => (this.news = data.articles))
			.catch((err) => {
				throw err;
			});
	},
};
</script>

<style></style>
