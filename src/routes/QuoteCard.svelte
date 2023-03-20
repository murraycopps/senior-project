<script>
	export let text = '';
    let top = text.includes('[top]');
</script>

<div class="flex flex-col gap-4 items-center {top ? "top" : "side"}">
	<p class="text-2xl font-bold text-center quote">{text.split('"')[1]}</p>
	<p class="text-xl font-bold text-center">{text.replace('[top]', '').split('"')[2]}</p>
</div>

<style>
    /* .side{
        position: relative;
        left: 50vw;
        transform: translateX(-50%);
        width: clamp(200px, 25vw, 500px);
    } */

    div{
		width: clamp(500px, 75vw, 1000px);

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
    .top{
        margin-bottom: 10rem;
    }

</style>
