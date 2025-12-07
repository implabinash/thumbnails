<script lang="ts">
	import { resolve } from "$app/paths";
	import * as htmlToImage from "html-to-image";

	let thumbnailEl: HTMLElement | null = null;

	async function downloadThumbnail() {
		if (!thumbnailEl) return;

		try {
			const dataUrl = await htmlToImage.toPng(thumbnailEl, {
				quality: 1,
				pixelRatio: 3
			});

			const link = document.createElement("a");
			link.download = "thumbnail.png";
			link.href = dataUrl;
			link.click();
		} catch (e) {
			console.error("Thumbnail export error:", e);
		}
	}
</script>

<section class="max-w-4xl mx-auto p-8 space-y-8">
	<div class="text-center">
		<a
			href={resolve("/")}
			class="text-2xl underline hover:bg-black hover:text-white hover:no-underline">Home</a
		>
	</div>

	<!-- bind:this={thumbnailEl} -->
	<!-- Thumbnail -->
	<div
		bind:this={thumbnailEl}
		class="w-full aspect-video bg-white border-4 border-black relative overflow-hidden"
	>
		<div class="grid grid-cols-2 h-full">
			<div class="border-r-4 border-b-4 border-black flex items-center justify-center">
				<div class="text-5xl uppercase">SQL</div>
			</div>
			<div class="border-b-4 border-black flex items-center justify-center bg-gray-50">
				<div class="text-5xl uppercase">Murder</div>
			</div>
			<div class="border-r-4 border-black flex items-center justify-center bg-gray-50">
				<div class="text-5xl uppercase">Mystery</div>
			</div>
			<div class="flex items-center justify-center bg-green-400">
				<div class="uppercase text-6xl">solved</div>
			</div>
		</div>
	</div>

	<!-- Download button -->
	<div class="text-center">
		<button
			onclick={downloadThumbnail}
			class="px-6 py-3 bg-blue-600 text-white border-2 border-black cursor-pointer hover:bg-blue-700"
		>
			Download Thumbnail (HD)
		</button>
	</div>
</section>
