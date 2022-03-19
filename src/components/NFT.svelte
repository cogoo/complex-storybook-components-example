<script>
	export let uri;
	fetchNFTImageUrl(uri);

	export let contain = false;
	export let cover = false;

	let src;

	async function fetchNFTImageUrl(url) {
		try {
			const response = await fetch(url);
			if (response.ok) {
				const result = await response.json();
				src = result.image;
			}
		} catch (err) {}
	}
</script>

<img {src} alt="" class:object-contain={contain} class:object-cover={cover} />
