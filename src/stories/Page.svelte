<script>
	import './page.css';
	import '../app.css';
	import NftViewer from '../components/NftViewer.svelte';
	import { Connection, clusterApiUrl } from '@solana/web3.js';

	const network = clusterApiUrl('mainnet-beta');
	const connection = new Connection(network);
	export let publicKey;
</script>

<article>
	<NftViewer {connection} {publicKey} />

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
