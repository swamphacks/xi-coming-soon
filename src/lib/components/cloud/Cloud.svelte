<script lang="ts">
	import { onMount } from "svelte";
	import gsap from "gsap";
	import cloud from '$lib/assets/cloud.png';

	let cloudObj: HTMLImageElement;
    const { windowWidth } = $props();
	
	const getRandomIntInclusive = (min: int, max: int) => {
		const minCeiled = Math.ceil(min);
		const maxFloored = Math.floor(max);
		return Math.floor(Math.random() * (maxFloored - minCeiled + 1) + minCeiled); 
	}

	onMount(() => {
		const cloudWidth = cloudObj.width;
		const duration = getRandomIntInclusive(5, 10);
		const tl = gsap.timeline();
		console.log(windowWidth, cloudWidth);
	    tl.fromTo(cloudObj, {x: cloudWidth}, { x: -windowWidth, ease: "none", duration: duration, repeat: -1 });
		tl.seek(1 + Math.floor(Math.random() * duration));
	 });
</script>

<img bind:this={cloudObj} src={cloud} alt="cloud" class="right-0 w-48 lg:w-80" />
