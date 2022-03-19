<script>
	import './page.css';
	import NftViewer from '../components/NftViewer.svelte';

	import { onMount } from 'svelte';
	import { clusterApiUrl } from '@solana/web3.js';
	import {
		workSpace,
		WalletProvider,
		WalletMultiButton,
		ConnectionProvider
	} from '@svelte-on-solana/wallet-adapter-ui';

	const localStorageKey = 'walletAdapter';
	const network = clusterApiUrl('devnet');

	let wallets;

	onMount(async () => {
		const { PhantomWalletAdapter } = await import('@solana/wallet-adapter-wallets');

		wallets = [new PhantomWalletAdapter()];
	});
</script>

<WalletProvider {localStorageKey} {wallets} />
<ConnectionProvider {network} />

<article>
	<WalletMultiButton />

	<NftViewer />

	<section>
		<h2>Pages in Storybook</h2>
		<p>
			The app itself only has one component `NftViewer`. This page (the wallet adapter + NftViewer)
			is contructed in the storybook file!
		</p>

		<ul>
			<li>Seperation of "example components" from your main app</li>
			<li>Your app has no notion that storybook exists</li>
			<li>Doesn't interupt your normal development flow</li>
			<li>Creating a page in storybook is no different to creating a page in your app</li>
		</ul>
	</section>
</article>
