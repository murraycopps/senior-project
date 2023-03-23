<script>
	import MovingShoes from "./MovingShoes.svelte";

	export let text = '';
	export let moving = false;
</script>

<div class="relative -mb-3 flex  flex-col mt-3 items-center {text.includes('[right]') ? "float-right ml-12 mr-2" : "float-left  mr-12 ml-2"} p-4 text-light-base rounded-2xl">
	{#if text.includes('[shoes]')}
		<MovingShoes {moving} />
	{/if}
	<p class="mb-4 text-2xl font-bold text-center quote">{text.split('"')[1]}</p>
		<p class="text-xl font-bold text-center">{text.replace('[quote]', '').replace('[right]', '').replace('[shoes]', '').split('"')[2]}</p>
</div>

<style>
	div {
		width: clamp(400px, 33vw, 800px);
        background-color: #051A4F;
        /* background-color: #132f75; */
	}
	.quote {
		font-style: italic;
	}
	.quote::before {
		content: open-quote;
		font-family: 'Times New Roman', Times, serif;
		font-size: 3rem;
		vertical-align: middle;
		position: relative;
		left: -0.3rem;
	}
	.quote::after {
		content: close-quote;
		font-family: 'Times New Roman', Times, serif;
		font-size: 3rem;
		vertical-align: middle;
		position: relative;
		right: -0.3rem;
	}
</style>
