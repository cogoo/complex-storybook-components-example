<script>
	import { Metadata } from '@metaplex-foundation/mpl-token-metadata';
	import { walletStore } from '@svelte-on-solana/wallet-adapter-core';
	import NFT from './NFT.svelte';

	export let connection;

	$: nftMetadata = Metadata.findDataByOwner(
		connection,
		$walletStore.publicKey || '7z7Q3UH4cMxSNDTATsQcC34rr4MVA9ydqpbeqnU4q7ba'
	);
</script>

<div class="relative inline-block text-left mt-10">
	<ul
		role="list"
		class="grid grid-cols-2 gap-x-4 gap-y-8 sm:grid-cols-3 sm:gap-x-6 lg:grid-cols-4 xl:gap-x-8"
	>
		{#await nftMetadata then value}
			{#if value}
				{#each value as nft}
					<li class="relative">
						<div
							class="group block w-full aspect-w-10 aspect-h-7 rounded-lg bg-gray-100 focus-within:ring-2 focus-within:ring-offset-2 focus-within:ring-offset-gray-100 focus-within:ring-indigo-500 overflow-hidden"
						>
							<NFT uri={nft.data.uri} cover />

							<button type="button" class="absolute inset-0 focus:outline-none">
								<span class="sr-only">View details for IMG_4985.HEIC</span>
							</button>
						</div>
						<p class="mt-2 block text-sm font-medium text-gray-900 truncate pointer-events-none">
							{nft.data.name}
						</p>
					</li>
				{/each}
			{/if}
		{/await}
	</ul>
</div>
