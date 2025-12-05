<script lang="ts">
	import { resolve } from '$app/paths';
	import * as htmlToImage from 'html-to-image';

	let thumbnailEl: HTMLElement | null = null;
	let timer = $state(64);
	let isGenerating = $state(false);
	let progress = $state('');

	async function downloadSingleThumbnail() {
		if (!thumbnailEl) return;

		try {
			const dataUrl = await htmlToImage.toPng(thumbnailEl, {
				quality: 1,
				pixelRatio: 3
			});

			const link = document.createElement('a');
			link.download = `thumbnail_${(127 - timer).toString().padStart(3, '0')}.png`;
			link.href = dataUrl;
			link.click();
		} catch (e) {
			console.error('Thumbnail export error:', e);
		}
	}

	async function downloadAllThumbnails() {
		if (!thumbnailEl || isGenerating) return;

		isGenerating = true;
		timer = 64;

		try {
			for (let i = 64; i >= 0; i--) {
				timer = i;
				progress = `Generating ${64 - i + 1}/128 (timer: ${i})`;

				// Wait for DOM to update
				await new Promise((resolve) => setTimeout(resolve, 100));

				// Generate and download
				const dataUrl = await htmlToImage.toPng(thumbnailEl, {
					quality: 1,
					pixelRatio: 3
				});

				const link = document.createElement('a');
				link.download = `thumbnail_${(64 - i).toString().padStart(3, '0')}.png`;
				link.href = dataUrl;
				link.click();

				// Small delay between downloads to prevent browser blocking
				await new Promise((resolve) => setTimeout(resolve, 50));
			}

			progress = 'Complete! All 128 images downloaded.';
		} catch (e) {
			console.error('Batch export error:', e);
			progress = `Error: ${e}`;
		} finally {
			isGenerating = false;
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

	<!-- Thumbnail -->
	<div
		bind:this={thumbnailEl}
		class="aspect-video w-full bg-black text-white grid place-items-center"
	>
		<div class="text-center space-y-12">
			<p class="text-3xl">starts in</p>
			<p class="font-bold text-9xl">{timer.toString(2).padStart(7, '0')}</p>
		</div>
	</div>

	<!-- Progress indicator -->
	{#if progress}
		<div class="text-center p-4 bg-gray-100 rounded">
			<p class="font-mono">{progress}</p>
		</div>
	{/if}

	<!-- Download buttons -->
	<div class="text-center space-x-4">
		<button
			onclick={downloadSingleThumbnail}
			disabled={isGenerating}
			class="px-6 py-3 bg-blue-600 text-white border-2 border-black cursor-pointer hover:bg-blue-700 disabled:bg-gray-400 disabled:cursor-not-allowed"
		>
			Download Current Frame
		</button>

		<button
			onclick={downloadAllThumbnails}
			disabled={isGenerating}
			class="px-6 py-3 bg-green-600 text-white border-2 border-black cursor-pointer hover:bg-green-700 disabled:bg-gray-400 disabled:cursor-not-allowed"
		>
			{isGenerating ? 'Generating...' : 'Download All 128 Frames'}
		</button>
	</div>

	<!-- Instructions -->
	<div class="bg-yellow-50 p-4 rounded border-2 border-yellow-300">
		<h3 class="font-bold mb-2">Instructions:</h3>
		<ol class="list-decimal list-inside space-y-1">
			<li>Click "Download All 128 Frames" to generate all images sequentially</li>
			<li>Wait for completion (takes ~30-60 seconds)</li>
			<li>Check your Downloads folder for all images</li>
			<li>
				Use with ffmpeg: <code class="bg-gray-200 px-2 py-1 rounded"
					>ffmpeg -framerate 30 -i thumbnail_%03d.png -c:v libx264 -pix_fmt yuv420p output.mp4</code
				>
			</li>
		</ol>
	</div>
</section>
