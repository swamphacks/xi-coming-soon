<script lang="ts">
	import { onMount } from "svelte";
	import gsap from "gsap";
	import car from '$lib/assets/car.png';

	// let carObj: HTMLImageElement;

	onMount(async () => {
	    // const tl = gsap.timeline();
	    gsap.to("img", { y: -5, duration: 0.1, repeatDelay: 1, repeat: -1, yoyo: true});
	});
</script>

<img src={car} alt="car" class={`${$$props.class || ''}`} />
