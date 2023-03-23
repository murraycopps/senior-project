<script>
	// import article and split it into an array of paragraphs
	import article from '$lib/scripts/article.js';
	import LandingImage from './LandingImage.svelte';
	import QuoteCard from './QuoteCard.svelte';
	import ShoeList from './ShoeList.svelte';
	import SideCard from './SideCard.svelte';
	import DataImage from '$lib/images/data.png';
	const paragraphs = article.split('\n').filter((p) => p.length > 0);

	let isTall = true;
	let isScrolling = false;

	const scrolling = () => {
		isScrolling = false;
	};

	const handleScroll = (e) => {
		isTall = e.target.scrollTop === 0;
		if (isScrolling) {
			clearTimeout(scrolling);
		}
		isScrolling = true;
		setTimeout(scrolling, 100);
	};
</script>

<title>Super Shoes</title>

<div
	class="flex flex-col gap-16 items-center h-screen overflow-y-scroll z-0 page {isTall
		? 'tall'
		: 'short'}"
	on:scroll={handleScroll}
>
	<LandingImage {isTall} />
	<ul class="relative flex flex-col items-center gap-16 pb-32">
		{#each paragraphs as paragraph, i}
			{#if paragraph.includes('[title]')}
				<h3 class="my-8 text-4xl font-bold text-center">{paragraph.replace('[title]', '')}</h3>
			{:else if paragraph.includes('[data]')}
				<div class="flex flex-col items-center gap-16 my-16">
					<h3 class="text-4xl font-bold text-center">
						Estimated change in race time, compared with a previous result, when switching shoes
					</h3>
					<div class="w-11/12 p-8 bg-white rounded-3xl">
						<img src={DataImage} alt="Data" />
					</div>
				</div>
			{:else if paragraph.includes('[image]')}
				<div class="flex flex-col items-center justify-center w-full gap-2">
					<img src={paragraph.match(/\{(.*?)\}/)[1]} alt="" class="w-3/4 rounded-3xl" />
					<p class="text-2xl text-center">
						{paragraph.replace(paragraph.match(/\{(.*?)\}/)[0], '').replace('[image]', '')}
					</p>
				</div>
			{:else if paragraph.includes('[quote]')}
				<QuoteCard text={paragraph.replace('[quote]', '')} />
			{:else if !paragraph.includes('[side]') && !paragraph.includes('[shoelist]')}
				{#if i > 0 && paragraphs[i - 1].includes('[side]')}
					<div
						class="side-container {paragraphs[i - 1].includes('[right]')
							? 'padding-left'
							: 'padding-right'}"
					>
						<SideCard text={paragraphs[i - 1].replace('[side]', '')} moving={isScrolling} />
						<p
							class="text-xl indent-12 leading-10 {paragraphs[i - 1].includes('[right]')
								? 'padding-right'
								: 'padding-left'} {paragraph.includes('[top]') && 'mb-12'}"
						>
							{paragraph.replace('[top]', '')}
						</p>
					</div>
				{:else if i > 0 && paragraphs[i - 1].includes('[shoelist]')}
					<div class="side-container padding-right">
						<ShoeList />
						<p class="text-xl leading-10 indent-12 padding-left">
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
		<div class="grid w-3/4 grid-cols-3 gap-4 text-2xl">
			<a
				href="/works-sited"
				class="flex flex-col items-center justify-center gap-4 p-8 text-light-base bg-mid-base hover:bg-dark-base rounded-3xl"
			>
				Works Sited
			</a>
			<a
				href="/images-sited"
				class="flex flex-col items-center justify-center gap-4 p-8 text-light-base bg-mid-base hover:bg-dark-base rounded-3xl"
			>
				Images Sited
			</a>
			<a
				href="/key-questions"
				class="flex flex-col items-center justify-center gap-4 p-8 text-light-base bg-mid-base hover:bg-dark-base rounded-3xl"
			>
				Key Questions
			</a>
		</div>
	</ul>
</div>

<style>
	a{
		transition: background-color 0.3s ease-in-out;
	}
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

	.padding-left {
		padding-left: var(--padding);
	}

	.padding-right {
		padding-right: var(--padding);
	}
</style>
