<script>
	// import article and split it into an array of paragraphs
	import article from '$lib/scripts/article.js';
	import LandingImage from './LandingImage.svelte';
	import QuoteCard from './QuoteCard.svelte';
	import ShoeList from './ShoeList.svelte';
	import SideCard from './SideCard.svelte';
	const paragraphs = article.split('\n').filter((p) => p.length > 0);

	let isTall = true;

	const handleScroll = (e) => {
		isTall = e.target.scrollTop === 0;
	};
	
</script>

<div
	class="flex flex-col gap-16 items-center h-screen overflow-y-scroll z-0 page {isTall
		? 'tall'
		: 'short'}"
	on:scroll={handleScroll}
>
	<LandingImage {isTall} />
	<ShoeList />
	<ul class="relative flex flex-col items-center gap-16 pb-32">
		{#each paragraphs as paragraph, i}
			{#if paragraph.includes('[title]')}
				<h3 class="my-8 text-4xl font-bold text-center">{paragraph.replace('[title]', '')}</h3>
			{:else if paragraph.includes('[quote]')}
				<QuoteCard text={paragraph.replace('[quote]', '')} />
			{:else if !paragraph.includes('[side]') && !paragraph.includes('[shoelist]')}
				{#if i > 0 && paragraphs[i - 1].includes('[side]')}
					<div class="side-container {paragraphs[i - 1].includes('[right]') ? "padding-left" : "padding-right"}">
						<SideCard text={paragraphs[i - 1].replace('[side]', '')} />
						<p class="text-xl indent-12 leading-10 {paragraphs[i - 1].includes('[right]') ? "padding-right" : "padding-left"} {paragraph.includes('[top]') && 'mb-12'}">
							{paragraph.replace('[top]', '')}
						</p>
					</div>
				{:else if i > 0 && paragraphs[i - 1].includes('[shoelist]')}
				<div class="side-container padding-left">
					<ShoeList />
					<p class="text-xl indent-12 leading-10 padding-right">
						{paragraph.replace('[top]', '')}
					</p>
				</div>
				{:else}
					<p class="text-xl indent-12 leading-10 {paragraph.includes('[top]') && 'mb-12'}">
						{paragraph.replace('[top]', '')}
					</p>
				{/if}
			{/if}
		{/each}
	</ul>
</div>

<style>
	div::-webkit-scrollbar {
		width: 0.5rem;
	}

	.page {
		--width: clamp(500px, 75vw, 1000px);
		--padding: calc((100vw - var(--width)) / 2);
		transition: padding 0.5s ease-in-out;
	}
	ul > * {
		width: var(--width);
		max-width: 100%;
	}
	.short {
		padding-top: 50vh;
		padding-top: 50svh;
	}
	.tall {
		padding-top: 100vh;
	}
	.side-container {
		width: 100%;
	}

	.padding-left{
		padding-left: var(--padding);
	}

	.padding-right{
		padding-right: var(--padding);

	}
</style>
