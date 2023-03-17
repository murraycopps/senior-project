<script>
	// import article and split it into an array of paragraphs
	import article from '$lib/scripts/article.js';
	import LandingImage from './LandingImage.svelte';
	const paragraphs = article.split('\n').filter((p) => p.length > 0);

    let isTall = true;


    const handleScroll = (e) => {
        isTall = e.target.scrollTop === 0;
        console.log(e.target.scrollTop)
    }
</script>

<div 
class="flex flex-col gap-16 items-center px-64 h-screen overflow-y-scroll z-0 bg-base {isTall ? "tall" : "short"}"
on:scroll={handleScroll}
>
    <LandingImage {isTall} />
	{#each paragraphs as paragraph}
		{#if paragraph.includes('[title]')}
            <h3 class="text-3xl text-center font-bold">{paragraph.replace('[title]', '')}</h3>
       {:else}
            <p class="text-xl indent-12">{paragraph}</p>
        {/if}
	{/each}
</div>

<style>
    /* style the divs scrollbar */
    div::-webkit-scrollbar {
        width: 0.5rem;
    }
    
    div{
        transition: padding 0.5s ease-in-out;
    }
    .short{
        padding-top: 50vh;
    }
    .tall{
        padding-top: 100vh;
    }

</style>