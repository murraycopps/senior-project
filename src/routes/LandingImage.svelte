<script>
	import LandingImage from '$lib/images/landing-image.svg';
	import { onMount } from 'svelte';

	export let isTall = true;
    let loading = true;

    onMount(() => {
        setTimeout(() => {
            loading = false;
        }, 500);
    });

</script>

<img src={LandingImage} alt="" class="{isTall ? 'tall' : 'short'} z-50 {loading && "loading"}"  />

<div class="{isTall ? 'tall' : 'short'} text-light-base z-50">
	<h1 class="{isTall ? 'text-8xl' : 'text-4xl'} text-center font-bold">The Rise of Super Shoes</h1>
	<h2 class="{isTall ? 'text-3xl' : 'text-xl'} text-center font-bold">
		Are They Necessary for Athletes to Compete at the World Stage?
	</h2>
</div>
<div
	class="p-4 byline fixed top-0 right-0 z-50 flex items-center justify-center {isTall
		? 'opacity-0 off-screen-right'
		: 'opacity-100'}"
>
	<h3 class="z-50 text-2xl text-center text-light-base">By: Murray Copps</h3>
</div>

<style>
	img {
		position: fixed;
		object-fit: cover;
		width: 100vw;
		transform-origin: 50% 100%;
		pointer-events: none;
	}

	img.tall {
		min-height: 85vh;
        animation: toTall 0.5s ease-in-out forwards;
	}

	img.short {
		min-height: 20vh;
        animation: toShort 0.5s ease-in-out forwards; 
	}

    img.loading{
        animation-duration: 0ms;
    }

	@keyframes toTall {
		0% {
			transform: scaleX(1.1) scaleY(0.4);
			bottom: 82vh;
		}
		100% {
			transform: scaleX(1.1) scaleY(1);
			bottom: 15vh;
		}
	}

    @keyframes toShort {
        0% {
            transform: scaleX(1.1) scaleY(1);
            bottom: 15vh;
        }
        100% {
            transform: scaleX(1.1) scaleY(0.4);
            bottom: 82vh;
        }
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

	div.tall {
		gap: 6rem;
		top: 35%;
		left: 50%;
		transform: translate(-50%, -50%);
	}
	div.short {
		top: 1rem;
		left: 2rem;
		gap: 1rem;
		max-height: 25vh;
	}

	div > * {
		transition: all 0.5s ease-in-out;
	}

	.byline {
		width: 25vw;
		height: 10vh;
	}
	.off-screen-right {
		transform: translateX(100%);
	}
</style>
