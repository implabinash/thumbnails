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
		class="w-full aspect-video bg-white border-4 border-black relative overflow-hidden flex"
	>
		<!-- Left side: Strikethrough list -->
		<div class="w-2/5 bg-gray-100 border-r-4 border-black flex flex-col justify-center pl-12">
			<div class="space-y-6">
				<div class="relative">
					<div class="text-gray-400 text-4xl">Learn SQL</div>
					<div class="absolute inset-0 flex items-center">
						<div class="w-full h-1 bg-red-600"></div>
					</div>
				</div>
				<div class="relative">
					<div class="text-gray-400 text-4xl">SQL Practice</div>
					<div class="absolute inset-0 flex items-center">
						<div class="w-full h-1 bg-red-600"></div>
					</div>
				</div>
				<div class="relative">
					<div class="text-gray-400 text-4xl">SQL Bootcamp</div>
					<div class="absolute inset-0 flex items-center">
						<div class="w-full h-1 bg-red-600"></div>
					</div>
				</div>
			</div>
		</div>

		<!-- Right side: Score -->
		<div class="w-3/5 flex items-center justify-center relative">
			<div class="space-y-10">
				<div class="text-black text-8xl mb-4">SQL</div>
				<div class="text-black text-8xl mb-4">Bolt</div>
			</div>

			<!-- <div class="absolute bottom-6 right-6 bg-red-500 text-white px-4 py-2 border-3 border-black">
				<div class="text-sm">Part: 02</div>
			</div> -->
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
