<script>
	import './page.css';
	import '../app.css';
	import NftViewer from '../components/NftViewer.svelte';
	import { clusterApiUrl } from '@solana/web3.js';

	const network = clusterApiUrl('mainnet-beta');

	import { onMount } from 'svelte';

	import {
		workSpace,
		WalletProvider,
		WalletMultiButton,
		ConnectionProvider
	} from '@svelte-on-solana/wallet-adapter-ui';

	const localStorageKey = 'walletAdapter';

	let wallets;

	onMount(async () => {
		const { PhantomWalletAdapter, SolflareWalletAdapter } = await import(
			'@solana/wallet-adapter-wallets'
		);

		wallets = [new PhantomWalletAdapter(), new SolflareWalletAdapter()];
	});
</script>

<WalletProvider {localStorageKey} {wallets} autoConnect />
<ConnectionProvider {network} />

<div class="tip-wrapper">
	<span class="tip">Tip</span>
	To use the wallet adapter, open the story in a new tab (icon top right)
</div>

<WalletMultiButton />

<NftViewer connection={$workSpace.connection} />
<!-- 
<section>
	<h2>Pages in Storybook</h2>
	<p>
		The app itself only has one component `NftViewer`. This page (the wallet adapter + NftViewer) is
		contructed in the storybook file!
	</p>

	<ul>
		<li>Seperation of "example components" from your main app</li>
		<li>Your app has no notion that storybook exists</li>
		<li>Doesn't interupt your normal development flow</li>
		<li>Creating a page in storybook is no different to creating a page in your app</li>
	</ul>
</section> -->
