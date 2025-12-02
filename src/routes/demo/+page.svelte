<script lang="ts">
	import { resolve } from '$app/paths';
	import * as htmlToImage from 'html-to-image';

	let thumbnailEl: HTMLElement | null = null;

	async function downloadThumbnail() {
		if (!thumbnailEl) return;

		try {
			const dataUrl = await htmlToImage.toPng(thumbnailEl, {
				quality: 1,
				pixelRatio: 3
			});

			const link = document.createElement('a');
			link.download = 'thumbnail.png';
			link.href = dataUrl;
			link.click();
		} catch (e) {
			console.error('Thumbnail export error:', e);
		}
	}
</script>

<section class="max-w-4xl mx-auto p-8 space-y-8">
	<div class="text-center">
		<a
			href={resolve('/')}
			class="text-2xl underline hover:bg-black hover:text-white hover:no-underline">Home</a
		>
	</div>

	<!-- bind:this={thumbnailEl} -->
	<!-- Thumbnail -->
	<div
		bind:this={thumbnailEl}
		class="w-full aspect-video bg-white border-4 border-black relative overflow-hidden"
	>
		<div class="absolute top-6 left-6 text-gray-500 text-base">[ FIRST STREAM ]</div>

		<div class="absolute top-6 right-6 bg-red-500 text-white px-4 py-2 border-3 border-black">
			<div class="text-sm">● LIVE</div>
		</div>

		<div class="absolute inset-0 flex flex-col items-center justify-center">
			<div class="text-blue-500 text-9xl mb-4 uppercase">Intro</div>
		</div>

		<div class="absolute bottom-8 left-8 text-black text-xl">[ THE OVERVIEW ]</div>
	</div>

	<!-- Download button -->
	<div class="text-center">
		<button
			on:click={downloadThumbnail}
			class="px-6 py-3 bg-blue-600 text-white border-2 border-black cursor-pointer hover:bg-blue-700"
		>
			Download Thumbnail (HD)
		</button>
	</div>
</section>
