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
		<div class="grid grid-cols-3 h-full">
			<div class="border-r-4 border-black flex flex-col items-center justify-center p-6">
				<div class="text-black text-5xl uppercase">weird</div>
			</div>
			<div class="border-r-4 border-black flex flex-col items-center justify-center p-6">
				<img
					alt="svgImg"
					src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciICB2aWV3Qm94PSIwIDAgNDggNDgiIHdpZHRoPSI0OHB4IiBoZWlnaHQ9IjQ4cHgiPjxwYXRoIGZpbGw9IiMzODhlM2MiIGQ9Ik0zOS41LDQyaC05Yy0xLDAtMS45LTAuNi0yLjMtMS41Yy0wLjQtMC45LTAuMi0yLDAuNS0yLjdsOC4zLTguM3YtMy45TDIxLjMsNDEuMyBjLTAuNSwwLjUtMS4xLDAuNy0xLjgsMC43aC0xMWMtMSwwLTEuOS0wLjYtMi4zLTEuNWMtMC40LTAuOS0wLjItMiwwLjUtMi43TDMzLjUsMTFoLTMuOUwxMC4zLDMwLjNjLTAuNywwLjctMS44LDAuOS0yLjcsMC41IEM2LjYsMzAuNCw2LDI5LjUsNiwyOC41di0xMWMwLTAuNywwLjMtMS4zLDAuNy0xLjhsNC43LTQuN2gtM0M3LjEsMTEsNiw5LjksNiw4LjVTNy4xLDYsOC41LDZoOWMxLDAsMS45LDAuNiwyLjMsMS41IGMwLjQsMC45LDAuMiwyLTAuNSwyLjdMMTEsMTguNXYzLjlMMjYuNyw2LjdDMjcuMiw2LjMsMjcuOCw2LDI4LjUsNmgxMWMxLDAsMS45LDAuNiwyLjMsMS41YzAuNCwwLjksMC4yLDItMC41LDIuN0wxNC41LDM3aDMuOSBsMTkuMy0xOS4zYzAuNy0wLjcsMS44LTAuOSwyLjctMC41YzAuOSwwLjQsMS41LDEuMywxLjUsMi4zdjExYzAsMC43LTAuMywxLjMtMC43LDEuOEwzNi41LDM3aDNjMS40LDAsMi41LDEuMSwyLjUsMi41IFM0MC45LDQyLDM5LjUsNDJ6Ii8+PC9zdmc+"
					class="size-64"
				/>
			</div>
			<div class="flex flex-col items-center justify-center p-6">
				<div class="text-black text-5xl mb-2 uppercase">use</div>
				<div class="text-black text-5xl uppercase">cases</div>
			</div>
		</div>
	</div>

	<!-- <div class="aspect-video w-full bg-black text-white grid place-items-center">
		<div class="text-center space-y-12">
			<p>starts in</p>

			<p class="font-bold text-9xl">{timer}</p>
		</div>
	</div> -->

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
