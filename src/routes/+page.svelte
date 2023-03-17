<script>
	// import article and split it into an array of paragraphs
	import article from '$lib/scripts/article.js';
	import LandingImage from './LandingImage.svelte';
	import QuoteCard from './QuoteCard.svelte';
	const paragraphs = article.split('\n').filter((p) => p.length > 0);

	let isTall = true;

	const handleScroll = (e) => {
		isTall = e.target.scrollTop === 0;
	};
</script>

<div
	class="flex flex-col gap-16 items-center h-screen overflow-y-scroll z-0 {isTall
		? 'tall'
		: 'short'}"
	on:scroll={handleScroll}
>
	<LandingImage {isTall} />
	<ul class="flex flex-col gap-16 items-center relative pb-32">
		{#each paragraphs as paragraph}
			{#if paragraph.includes('[title]')}
				<h3 class="text-4xl text-center font-bold my-8">{paragraph.replace('[title]', '')}</h3>
			{:else if paragraph.includes('[quote]')}
				<QuoteCard text={paragraph.replace('[quote]', '')} />
			{:else}
				<p class="text-xl indent-12 leading-10 {paragraph.includes('[top]') && "mb-12"}">{paragraph.replace('[top]', '')}</p>
			{/if}
		{/each}
	</ul>
</div>

<style>
	div::-webkit-scrollbar {
		width: 0.5rem;
	}

	div {
		transition: padding 0.5s ease-in-out;
	}
    ul{
        width: clamp(500px, 75vw, 1000px);
		max-width: 100%;
    }
	.short {
		padding-top: 50vh;
		padding-top: 50svh;
	}
	.tall {
		padding-top: 100vh;
	}
</style>
