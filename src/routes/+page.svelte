<script lang="ts">
	import { resolve } from "$app/paths";
</script>

<section class="max-w-4xl mx-auto p-8 space-y-8">
	<div class="text-center">
		<a
			href={resolve("/demo")}
			class="text-2xl underline hover:bg-black hover:text-white hover:no-underline">Demo</a
		>
	</div>

	<div class="w-full aspect-video bg-white border-4 border-black relative overflow-hidden">
		<div class="grid grid-cols-3 h-full">
			<div
				class="border-r-4 border-black bg-gray-100 flex flex-col items-center justify-center p-6"
			>
				<div class="text-gray-500 text-sm mb-2">PHASE 1</div>
				<div class="text-black text-4xl mb-2">THE</div>
				<div class="text-black text-4xl">PROBLEM</div>
			</div>
			<div class="border-r-4 border-black bg-gray-50 flex flex-col items-center justify-center p-6">
				<div class="text-blue-500 text-sm mb-2">PHASE 2</div>
				<div class="text-black text-4xl mb-2">THE</div>
				<div class="text-black text-4xl">SOLUTION</div>
			</div>
			<div class="bg-yellow-400 flex flex-col items-center justify-center p-6">
				<div class="text-black text-sm mb-2">PHASE 3</div>
				<div class="text-black text-4xl mb-2">THE</div>
				<div class="text-black text-4xl">FUTURE</div>
			</div>
		</div>

		<div
			class="absolute top-6 left-1/2 -translate-x-1/2 bg-red-500 text-white px-6 py-2 border-3 border-black"
		>
			<div class="text-lg">● LIVE</div>
		</div>
	</div>

	<div class="w-full aspect-video bg-white border-4 border-black relative overflow-hidden flex">
		<!-- Left side: Strikethrough list -->
		<div class="w-2/5 bg-gray-100 border-r-4 border-black flex flex-col justify-center pl-12">
			<div class="space-y-6">
				<div class="relative">
					<div class="text-gray-400 text-3xl">Vibes</div>
					<div class="absolute inset-0 flex items-center">
						<div class="w-full h-1 bg-red-600"></div>
					</div>
				</div>
				<div class="relative">
					<div class="text-gray-400 text-3xl">Politics</div>
					<div class="absolute inset-0 flex items-center">
						<div class="w-full h-1 bg-red-600"></div>
					</div>
				</div>
				<div class="relative">
					<div class="text-gray-400 text-3xl">Hype</div>
					<div class="absolute inset-0 flex items-center">
						<div class="w-full h-1 bg-red-600"></div>
					</div>
				</div>
			</div>
		</div>

		<!-- Right side: Score -->
		<div class="w-3/5 flex items-center justify-center relative">
			<div class="text-center">
				<div class="text-black text-9xl mb-4">92.5</div>
				<div class="text-yellow-400 text-4xl">IMPACT SCORE</div>
			</div>

			<div class="absolute top-6 right-6 bg-black text-white px-6 py-3 border-3 border-black">
				<div class="text-sm">PRIORITY: CRITICAL</div>
			</div>
		</div>
	</div>

	<div class="w-full aspect-video bg-white border-4 border-black relative overflow-hidden">
		<div class="grid grid-cols-2 h-full">
			<div class="border-r-4 border-b-4 border-black flex items-center justify-center">
				<div class="text-gray-400 text-4xl">BUSY</div>
			</div>
			<div class="border-b-4 border-black flex items-center justify-center bg-gray-50">
				<div class="text-gray-400 text-4xl">URGENT</div>
			</div>
			<div class="border-r-4 border-black flex items-center justify-center bg-gray-50">
				<div class="text-gray-400 text-4xl">LATER</div>
			</div>
			<div class="flex items-center justify-center bg-yellow-400">
				<div class="text-black text-6xl">IMPACT</div>
			</div>
		</div>

		<div class="absolute top-6 left-6 text-black text-sm">[ PRIORITY MATRIX ]</div>
	</div>

	<div class="w-full aspect-video bg-white border-4 border-black relative overflow-hidden">
		<div class="absolute top-6 left-6 text-gray-500 text-base">[ FIRST STREAM ]</div>

		<div class="absolute top-6 right-6 bg-red-500 text-white px-4 py-2 border-3 border-black">
			<div class="text-sm">● LIVE</div>
		</div>

		<div class="absolute inset-0 flex flex-col items-center justify-center">
			<div class="text-black text-5xl mb-4">INTRODUCING</div>
			<div class="text-yellow-400 text-9xl mb-4">DRIM</div>
			<div class="text-black text-3xl">DevRel Impact Model</div>
		</div>

		<div class="absolute bottom-8 left-8 text-black text-xl">[ THE OVERVIEW ]</div>
	</div>

	<div class="w-full aspect-video bg-white border-4 border-black relative overflow-hidden">
		<div class="absolute top-6 right-6 bg-red-500 text-white px-4 py-2 border-3 border-black">
			<div class="text-sm">● LIVE</div>
		</div>

		<div class="grid grid-cols-2 h-full">
			<!-- Problem Side -->
			<div class="border-r-4 border-black flex flex-col items-center justify-center bg-gray-50 p-8">
				<div class="text-gray-400 text-2xl mb-6">THE PROBLEM</div>
				<div class="space-y-3 w-full">
					<div class="relative">
						<div class="text-gray-400 text-2xl">Vibes</div>
						<div class="absolute inset-0 flex items-center">
							<div class="w-full h-1 bg-red-500"></div>
						</div>
					</div>
					<div class="relative">
						<div class="text-gray-400 text-2xl">Guessing</div>
						<div class="absolute inset-0 flex items-center">
							<div class="w-full h-1 bg-red-500"></div>
						</div>
					</div>
					<div class="relative">
						<div class="text-gray-400 text-2xl">Politics</div>
						<div class="absolute inset-0 flex items-center">
							<div class="w-full h-1 bg-red-500"></div>
						</div>
					</div>
				</div>
			</div>

			<!-- Solution Side -->
			<div class="flex flex-col items-center justify-center p-8">
				<div class="text-black text-2xl mb-6">THE SOLUTION</div>
				<div class="text-yellow-400 text-8xl mb-4">DRIM</div>
				<div class="text-black text-xl">(D×R×I)/M</div>
			</div>
		</div>
	</div>

	<!-- 1. Postgres Day 1 -->
	<div class="w-full aspect-video bg-blue-600 relative overflow-hidden">
		<div class="absolute inset-0 flex flex-col items-center justify-center">
			<div class="text-white text-6xl font-black mb-4">POSTGRES</div>
			<div class="text-white text-9xl font-black">01</div>
		</div>
		<div class="absolute bottom-8 left-8 text-white text-xl opacity-80">Getting Started</div>
	</div>

	<!-- 2. Postgres Indexing -->
	<div class="w-full aspect-video bg-white relative overflow-hidden">
		<div class="absolute inset-0 flex items-center justify-center">
			<div class="text-center">
				<div class="text-gray-400 text-3xl font-normal mb-4">postgres</div>
				<div class="text-black text-9xl font-black">INDEX</div>
			</div>
		</div>
	</div>

	<!-- 3. Postgres Query -->
	<div class="w-full aspect-video bg-black relative overflow-hidden">
		<div class="absolute inset-0 flex items-center justify-center px-12">
			<div class="text-center">
				<div class="text-gray-400 text-4xl font-mono mb-4">SELECT *</div>
				<div class="text-white text-7xl font-black">POSTGRES</div>
				<div class="text-gray-400 text-4xl font-mono mt-4">FROM basics</div>
			</div>
		</div>
	</div>

	<!-- 8. SQL Challenge Format -->
	<div class="w-full aspect-video bg-black relative overflow-hidden">
		<div class="absolute inset-0 flex flex-col items-center justify-center">
			<div class="text-green-400 text-4xl font-mono mb-6">advent_of_sql</div>
			<div class="text-white text-9xl font-black">12</div>
		</div>
		<div class="absolute top-8 left-8 text-green-400 text-sm font-mono">⭐ challenge</div>
	</div>

	<!-- 5. SQL Daily Challenge -->
	<div class="w-full aspect-video bg-white relative overflow-hidden">
		<div class="absolute inset-0 flex items-center justify-center">
			<div class="text-center">
				<div class="text-gray-400 text-3xl mb-2">DAY</div>
				<div class="text-black text-9xl font-black">07</div>
				<div class="bg-green-500 text-white px-6 py-2 text-2xl font-bold mt-4 inline-block">
					SOLVED
				</div>
			</div>
		</div>
	</div>

	<!-- 7. Query Time -->
	<div class="w-full aspect-video bg-black relative overflow-hidden">
		<div class="absolute inset-0 flex flex-col items-center justify-center">
			<div class="text-gray-400 text-3xl mb-4">execution time:</div>
			<div class="text-green-400 text-9xl font-black mono">0.3ms</div>
			<div class="text-white text-3xl mt-4">OPTIMIZED</div>
		</div>
	</div>
</section>
