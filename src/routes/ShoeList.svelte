<script>
	const shoes = [
		{
			distance: 'Track Distance',
			shoes: [
				{ shoe: 'ZoomX Dragonfly', brand: 'nike' },
				{ shoe: 'Air Zoom Victory', brand: 'nike' },
				{ shoe: 'Adizero Avanti TYO', brand: 'adidas' },
				{ shoe: 'FuelCell LD', brand: 'new' },
				{ shoe: 'Cielo X 2 LD', brand: 'hoka' }
			]
		},
		{
			distance: 'Track Intervals',
			shoes: [
				{ shoe: 'ZoomX Streakfly', brand: 'nike' },
				{ shoe: 'ZoomX Vaporfly Next% 2', brand: 'nike' },
				{ shoe: 'Adizero Takumi Sen 9', brand: 'adidas' },
				{ shoe: 'ZoomX Vaporfly 3', brand: 'nike' },
				{ shoe: 'MetaSpeed Sky', brand: 'asics' }
			]
		},
		{
			distance: '5k/10k',
			shoes: [
				{ shoe: 'ZoomX Vaporfly Next% 2', brand: 'nike' },
				{ shoe: 'Adizero Takumi Sen 9', brand: 'adidas' },
				{ shoe: 'ZoomX Vaporfly Next% 3', brand: 'nike' },
				{ shoe: 'MetaSpeed Sky+', brand: 'asics' },
				{ shoe: 'ZoomX Streakfly', brand: 'nike' }
			]
		},
		{
			distance: 'Half Marathon',
			shoes: [
				{ shoe: 'ZoomX Vaporfly Next% 3', brand: 'nike' },
				{ shoe: 'ZoomX Vaporfly Next% 2', brand: 'nike' },
				{ shoe: 'ZoomX Alphafly Next%', brand: 'nike' },
				{ shoe: 'ZoomX Alphafly Next% 2', brand: 'nike' },
				{ shoe: 'MetaSpeed Sky+', brand: 'asics' }
			]
		},
		{
			distance: 'Marathon',
			shoes: [
				{ shoe: 'ZoomX Alphafly Next% 2', brand: 'nike' },
				{ shoe: 'ZoomX Alphafly Next%', brand: 'nike' },
				{ shoe: 'ZoomX Vaporfly Next% 3', brand: 'nike' },
				{ shoe: 'ZoomX Vaporfly Next% 2', brand: 'nike' },
				{ shoe: 'Adizero Pro 3', brand: 'adidas' }
			]
		}
	];

	let index = 0;
	let left = false;
	let right = false;
	let pastHalfway = false;
</script>

<div
	class="flex flex-col items-center float-left gap-4 p-4 ml-2 mr-12 overflow-x-hidden text-white width rounded-2xl"
>
	<h2 class="text-4xl font-bold text-center">Fastest Shoes</h2>
	<div class="flex flex-row items-center justify-center gap-2">
		<button
			on:click={() => {
				if (left || right) return;
				left = true;
				setTimeout(() => {
					pastHalfway = true;
				}, 500);
				setTimeout(() => {
					left = false;
					pastHalfway = false;
					if (index > 0) index--;
					else index = shoes.length - 1;
				}, 1000);
			}}
		>
			<svg
				class="w-12 h-12 scale-150 rotate-90"
				viewBox="0 0 24 24"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M7 10L12 15L17 10"
					stroke="white"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
		</button>

		<p class="w-64 text-4xl text-center {(left || right) && 'fade-change'}">
			{shoes[pastHalfway ? (left ? (index > 0? index - 1 : shoes.length - 1) : (index < shoes.length - 1 ? index + 1 : 0)) : index].distance}
		</p>

		<button
			on:click={() => {
				if (left || right) return;
				right = true;
				setTimeout(() => {
					pastHalfway = true;
				}, 500);
				setTimeout(() => {
					right = false;
					pastHalfway = false;
					if (index < shoes.length - 1) index++;
					else index = 0;
				}, 1000);
			}}
		>
			<svg
				class="w-12 h-12 scale-150 -rotate-90"
				viewBox="0 0 24 24"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M7 10L12 15L17 10"
					stroke="white"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
		</button>
	</div>
	<div class={`display grid place-items-center ${left && 'left'} ${right && 'right'}`}>
		<ul class="flex flex-col gap-2 text-2xl w-fit">
			{#each shoes.at(index - 1).shoes as shoe}
				<li class={shoe.brand}>
					{shoe.shoe}
				</li>
			{/each}
		</ul>
		<ul class="flex flex-col gap-2 text-2xl">
			{#each shoes[index].shoes as shoe}
				<li class={shoe.brand}>
					{shoe.shoe}
				</li>
			{/each}
		</ul>
		<ul class="flex flex-col gap-2 text-2xl">
			{#each shoes.at(index < shoes.length - 1 ? index + 1 : 0).shoes as shoe}
				<li class={shoe.brand}>
					{shoe.shoe}
				</li>
			{/each}
		</ul>
	</div>
</div>

<style>
	.fade-change {
		/* make an animation to fade it out then make a second to fade it back in. it should take a total of 1 second. use fade-in-out */
		animation: fade 0.5s ease-in-out 0s, fade-reverse 0.5s ease-in-out 0.5s
	}

	@keyframes fade {
		0% {
			opacity: 1;
		}
		100% {
			opacity: 0;
		}
	}

	@keyframes fade-reverse {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}
	.width {
		width: 24rem;
		min-height: 24rem;
		background-color: #051a4f;
	}
	.display {
		grid-template-columns: repeat(3, 24rem);
	}

	.left {
		animation: left 1s ease-in-out;
	}
	.right {
		animation: right 1s ease-in-out;
	}

	@keyframes left {
		0% {
			transform: translateX(0);
		}
		100% {
			transform: translateX(24rem);
		}
	}

	@keyframes right {
		0% {
			transform: translateX(0);
		}
		100% {
			transform: translateX(-24rem);
		}
	}
	li {
		background-repeat: no-repeat;
		background-position: left center;
		width: fit-content;
	}
	li::before {
		content: '';
		width: 2rem;
		height: 2rem;
		display: inline-block;
		background-repeat: no-repeat;
		background-position: left bottom;
		margin-right: 1.5rem;
		filter: invert();
	}
	.nike::before {
		background-image: url($lib/images/nike.png);
		background-size: 2rem;
	}
	.adidas::before {
		background-image: url($lib/images/adidas.png);
		background-size: 1.75rem;
	}

	.asics::before {
		background-image: url($lib/images/asics.png);
		background-size: 1.25rem;
	}

	.new::before {
		background-image: url($lib/images/new.png);
		background-size: 1.75rem;
	}

	.hoka::before {
		background-image: url($lib/images/hoka.png);
		background-size: 2.125rem;
		background-position: left 75%;
	}
</style>
