<script lang="ts">
	import { onMount } from "svelte";
	import gsap from "gsap";
	import car from '$lib/assets/car.png';

	let carObj: HTMLImageElement;

	onMount(async () => {
	    const tl = gsap.timeline({ repeat: -1, repeatDelay: 1, repeatRefresh: true });
	    tl.set(carObj, { y: -3, delay: 1 })
	      .set(carObj, { y: 3, delay: 0.2 })
		;
	});
</script>

<img bind:this={carObj} src={car} alt="car" class={`${$$props.class || ''}`} />
