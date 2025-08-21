<main class="relative h-screen w-screen overflow-hidden bg-sky font-overpass">
	<!-- Ground with curved top -->
	<div class="absolute bottom-0 hidden h-full w-screen md:flex">
		<svg class="absolute bottom-0 h-[40%] w-full" viewBox="0 0 100 30" preserveAspectRatio="none">
			<path d="M0,10 Q50,0 100,10 L100,30 L0,30 Z" fill="#B4CF9B" />
		</svg>

		<!-- ROAD -->
		<img class="absolute bottom-0 left-0 h-[31.5%]" src="/road.svg" alt="Road SVG" />
	</div>

	<!-- Orad sign -->

	<!-- Mobile grass -->
	<div class="absolute bottom-0 h-1/3 w-screen bg-grass"></div>

	<!-- Mobile Signs -->
	<div
		class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-5/6"
	>
		<div class="flex flex-col rounded-xl min-h-[30vh] w-[80vw] justify-center items-center border-6 border-white bg-interstate-green">
			<!-- Inner container-->
			<div class="flex flex-col justify-center gap-8 px-12">
				<div class="flex flex-row items-center gap-2">
					<img
						class="h-16"
						src="/interstate_logo_sh.svg"
						alt="Interstate logo with SwampHacks Logo"
					/>
					<h2 class="text-center text-white font-medium">University of Florida's Flagship Hackathon</h2>
				</div>
				<h1 class="text-3xl tracking-wide text-white text-center font-extrabold">SWAMPHACKS XI</h1>
				<h2 class="text-xl text-white text-center font-medium">160 DAYS</h2>
			</div>
		</div>
		<!-- Signposts -->
		<div class="flex flex-col rounded-xl min-h-[6vh] w-[80vw] justify-center mt-3 border-6 border-white bg-interstate-green">
			<p class="text-xl text-white text-center font-extrabold">JOIN MAILING LIST</p>

		</div>
		<div class="block min-w-max fill-signpost-gray">
			<div class="absolute left-1/5 -translate-y-1/5 -z-1">
				<svg class="min-h-screen" width="15" xmlns="http://www.w3.org/2000/svg">
					<rect width="15" height="1000"></rect>
				</svg>
			</div>
			<div class="absolute right-1/5 -translate-y-1/5 -z-1">
				<svg class="min-h-screen" width="15" xmlns="http://www.w3.org/2000/svg">
					<rect width="15" height="1000"></rect>
				</svg>
			</div>
		</div>
	</div>
</main>
