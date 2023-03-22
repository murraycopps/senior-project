<script>
	const shoes = [
		{
			distance: 'Track',
			shoes: [
				{ shoe: 'ZoomX Dragonfly', brand: 'nike' },
				{ shoe: 'Air Zoom Victory', brand: 'nike' },
				{ shoe: 'Adizero Avanti TYO', brand: 'adidas' },
				{ shoe: 'FuelCell LD', brand: 'new' },
				{ shoe: 'Cielo X 2 LD', brand: 'hoka' },
			]
		},
		{
			distance: 'Track Intervals',
			shoes: [
				
				{ shoe: 'ZoomX Streakfly', brand: 'nike' },
				{ shoe: 'ZoomX Vaporfly Next% 2', brand: 'nike' },
				{ shoe: 'Adizero Takumi Sen 9', brand: 'adidas' },
				{ shoe: 'ZoomX Vaporfly 3', brand: 'nike' },
				{ shoe: 'MetaSpeed Sky', brand: 'asics' },
				
			]
		},
		{
			distance: '5k/10k',
			shoes: [
				{ shoe: 'ZoomX Vaporfly Next% 2', brand: 'nike' },
				{ shoe: 'Adizero Takumi Sen 9', brand: 'adidas' },
				{ shoe: 'ZoomX Vaporfly Next% 3', brand: 'nike' },
				{ shoe: 'MetaSpeed Sky+', brand: 'asics' },
				{ shoe: 'ZoomX Streakfly', brand: 'nike' },
			]
		},
		{
			distance: 'Half Marathon',
			shoes: [
				{ shoe: 'ZoomX Vaporfly Next% 3', brand: 'nike' },
				{ shoe: 'ZoomX Vaporfly Next% 2', brand: 'nike' },
				{ shoe: 'ZoomX Alphafly Next%', brand: 'nike' },
				{ shoe: 'ZoomX Alphafly Next% 2', brand: 'nike' },
				{ shoe: 'MetaSpeed Sky+', brand: 'asics' },
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
</script>

<div class="flex flex-col float-right gap-4 p-4">
	<h2 class="text-4xl font-bold text-center">Fastest Shoes</h2>
	<div class="flex flex-row items-center justify-center gap-2">
		<button
			on:click={() => {
				if (index > 0) index--;
				else index = shoes.length - 1;
			}}
		>
			<svg
				class="w-16 h-16 rotate-90"
				viewBox="0 0 24 24"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M7 10L12 15L17 10"
					stroke="black"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
		</button>

		<p class="w-64 text-4xl text-center">
			{shoes[index].distance}
		</p>

		<button
			on:click={() => {
				if (index < shoes.length - 1) index++;
				else index = 0;
			}}
		>
			<svg
				class="w-16 h-16 -rotate-90"
				viewBox="0 0 24 24"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M7 10L12 15L17 10"
					stroke="black"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
		</button>
	</div>
	<ul class="text-2xl pl-12 flex flex-col gap-2">
		{#each shoes[index].shoes as shoe}
			<li class={shoe.brand}>
				{shoe.shoe}
			</li>
		{/each}
	</ul>
</div>

<style>
	li {
		background-repeat: no-repeat;
		background-position: left center;
	}
	li::before{
		content: "";
		width: 2rem;
		height: 2rem;
		display: inline-block;
		background-repeat: no-repeat;
		background-position: left bottom;
		margin-right: 1.5rem;
	}
	.nike::before{
		background-image: url($lib/images/nike.png);
		background-size: 2rem;
	}
	.adidas::before{
		background-image: url($lib/images/adidas.png);
		background-size: 1.75rem;
	}

	.asics::before{
		background-image: url($lib/images/asics.png);
		background-size: 1.25rem;
	}

	.new::before{
		background-image: url($lib/images/new.png);
		background-size: 1.75rem;
	}

	.hoka::before{
		background-image: url($lib/images/hoka.png);
		background-size: 2.125rem;
		background-position: left 75%;
	}
</style>
