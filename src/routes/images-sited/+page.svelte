<script>
    import article from '$lib/scripts/article.js';
    const images = article.split('\n').filter((p) => p.length > 0 && p.includes('[image]')).map((p) => p.match(/\{(.*?)\}/)[1]);
</script>

<title>Images Cited</title>

 <div class="flex flex-col items-center w-screen h-screen gap-4 p-4 justify-evenly">
	<h1 class="text-4xl text-center">Images Cited</h1>
	<ul class="flex flex-col gap-4 px-16 text-xl">
        {#each images as image}
            <li>{image}</li>
        {/each}
        <li>https://www.nytimes.com/interactive/2019/12/13/upshot/nike-vaporfly-next-percent-shoe-estimates.html</li>
	</ul>
</div>
<a
	href="/"
	class="absolute px-8 py-4 text-3xl rounded-lg top-2 left-2 bg-mid-base hover:bg-dark-base text-light-base"
	>Home</a
>

<style>
    a{
		transition: background-color 0.3s ease-in-out;
	}
</style>