<main class="relative h-screen w-screen overflow-hidden bg-sky font-overpass">
	<!-- Ground with curved top -->
	<div class="absolute bottom-0 hidden h-full w-screen md:flex">
		<svg class="absolute bottom-0 h-[40%] w-full" viewBox="0 0 100 30" preserveAspectRatio="none">
			<path d="M0,10 Q50,0 100,10 L100,30 L0,30 Z" fill="#6EC21D" />
		</svg>

		<!-- ROAD -->
		<img class="absolute bottom-0 left-0 h-[31.5%]" src="/road.svg" alt="Road SVG" />
	</div>

	<!-- Orad sign -->

	<!-- Mobile grass -->
	<div class="absolute bottom-0 h-1/3 w-screen bg-grass"></div>

	<!-- Mobile Sign -->
	<div
		class="absolute top-1/2 left-1/2 flex min-h-[30vh] w-[80vw] -translate-x-1/2 -translate-y-5/6 transform flex-col rounded-xl border-6 border-white bg-interstate-green"
	>
		<!-- Inner container-->
		<div class="relative flex w-full flex-1 flex-col justify-center gap-8 px-8">
			<div class="flex flex-row items-center gap-6">
				<img
					class="h-16"
					src="/interstate_logo_sh.svg"
					alt="Interstate logo with SwampHacks Logo"
				/>
				<h2 class="text-center text-white">University of Florida's Flagship Hackathon</h2>
			</div>
			<h1 class="text-3xl font-semibold tracking-wide text-white">SwampHacks XI</h1>
		</div>

		<!-- Exit only sign-->
		<!-- Exit only sign -->
		<div
			class="absolute bottom-0 h-12 w-full rounded-b-md bg-yellow-300 flex flex-row justify-between items-center"	
		></div>
		<!-- Pole 1 -->
		<div></div>

		<!-- Pole 2 -->
		<div></div>
	</div>
</main>
