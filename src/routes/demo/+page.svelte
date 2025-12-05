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
		<div class="grid grid-cols-3 h-full">
			<div class="border-r-4 border-black flex flex-col items-center justify-center p-6">
				<div class="text-black text-5xl mb-2 uppercase">weird</div>
			</div>
			<div class="border-r-4 border-black flex flex-col items-center justify-center p-6">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					x="0px"
					y="0px"
					width="256"
					height="256"
					viewBox="0 0 48 48"
				>
					<path
						fill="#388e3c"
						d="M39.5,42h-9c-1,0-1.9-0.6-2.3-1.5c-0.4-0.9-0.2-2,0.5-2.7l8.3-8.3v-3.9L21.3,41.3 c-0.5,0.5-1.1,0.7-1.8,0.7h-11c-1,0-1.9-0.6-2.3-1.5c-0.4-0.9-0.2-2,0.5-2.7L33.5,11h-3.9L10.3,30.3c-0.7,0.7-1.8,0.9-2.7,0.5 C6.6,30.4,6,29.5,6,28.5v-11c0-0.7,0.3-1.3,0.7-1.8l4.7-4.7h-3C7.1,11,6,9.9,6,8.5S7.1,6,8.5,6h9c1,0,1.9,0.6,2.3,1.5 c0.4,0.9,0.2,2-0.5,2.7L11,18.5v3.9L26.7,6.7C27.2,6.3,27.8,6,28.5,6h11c1,0,1.9,0.6,2.3,1.5c0.4,0.9,0.2,2-0.5,2.7L14.5,37h3.9 l19.3-19.3c0.7-0.7,1.8-0.9,2.7-0.5c0.9,0.4,1.5,1.3,1.5,2.3v11c0,0.7-0.3,1.3-0.7,1.8L36.5,37h3c1.4,0,2.5,1.1,2.5,2.5 S40.9,42,39.5,42z"
					></path>
				</svg>
			</div>
			<div class="flex flex-col items-center justify-center p-6">
				<div class="text-black text-5xl mb-2 uppercase">use</div>
				<div class="text-black text-5xl mb-2 uppercase">cases</div>
			</div>
		</div>

		<div
			class="absolute bottom-6 left-1/2 -translate-x-1/2 bg-red-500 text-white px-6 py-2 border-3 border-black"
		>
			<div class="text-lg uppercase">part: 02</div>
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
