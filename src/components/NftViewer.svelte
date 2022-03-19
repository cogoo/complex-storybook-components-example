<script>
	import { walletStore } from '@svelte-on-solana/wallet-adapter-core';

	$: {
		console.log($walletStore.publicKey);
	}
</script>

{$walletStore.publicKey}
