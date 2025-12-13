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
	<div bind:this={thumbnailEl} class="w-full aspect-video bg-black relative overflow-hidden">
		<!-- <div class="absolute top-8 left-8 text-green-400 text-sm font-mono">part: 01</div> -->

		<div class="absolute inset-0 flex items-center justify-center px-12">
			<div class="space-y-6">
				<div class="text-4xl font-bold text-blue-400">SELECT</div>
				<div class="text-white text-7xl font-black indent-16">basics</div>
				<div class="text-blue-400 text-4xl font-bold">FROM</div>
				<div class="text-white text-7xl font-black indent-16">postgres;</div>
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
