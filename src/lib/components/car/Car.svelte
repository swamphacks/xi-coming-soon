<script lang="ts">
	// import { onMount } from "svelte";
	// import gsap from "gsap";
	import car from '/assets/car.png';

	// // let carObj: HTMLImageElement;

	// onMount(async () => {
	//     const tl = gsap.timeline();
	//     tl.to("img", { rotation: 27 });
	// });
</script>

<img src={car} alt="car" class={`${$$props.class || ''}`} />
