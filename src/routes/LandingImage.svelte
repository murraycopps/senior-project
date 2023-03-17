<script>
	import LandingImage from '$lib/images/landing-image3.svg';

	export let isTall = true;
</script>

<img src={LandingImage} alt="" class="{isTall ? 'tall' : 'short'} z-50" />

<div class="{isTall ? 'tall' : 'short'} text-gray-200 z-50">
	<h1 class="{isTall ? 'text-8xl' : 'text-4xl'} text-center font-bold">The Rise of Super Shoes</h1>
	<h2 class="{isTall ? 'text-3xl' : 'text-xl'} text-center font-bold">
		Are They Necessary for Athletes to Compete at the World Stage?
	</h2>
</div>
<div class="p-4 byline fixed top-0 right-0 z-50 flex items-center justify-center {isTall ? "opacity-0 off-screen-right" : "opacity-100"}">
	<h3 class="text-2xl text-center text-gray-200 z-50">By: Murray Copps</h3>
</div>

<style>
	img {
		position: fixed;
		object-fit: cover;
		width: 100vw;
		transform: scaleX(1.1);
		transition: all 0.5s ease-in-out;
		transform-origin: 50% 100%;
		pointer-events: none;
	}
	div {
		transition: all 0.5s ease-in-out;
		position: fixed;
		display: flex;
		align-items: center;
		position: fixed;
		width: max-content;
		flex-direction: column;
		pointer-events: none;
	}
	img.tall {
		bottom: 15vh;
		min-height: 85vh;
	}
	img.short {
		min-height: 20vh;
		bottom: 80vh;
		transform: scaleX(1.1) scaleY(0.5);
	}

	div.tall {
		gap: 6rem;
		top: 35%;
		left: 50%;
		transform: translate(-50%, -50%);
	}
	div.short {
		top: 1rem;
		left: 2rem;
		gap: 2rem;
		max-height: 25vh;
	}

	div > * {
		transition: all 0.5s ease-in-out;
	}

	.byline {
		width: 25vw;
		height: 10vh;
	}
    .off-screen-right{
        transform: translateX(100%);
    }
</style>
