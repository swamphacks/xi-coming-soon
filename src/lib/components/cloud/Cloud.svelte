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
	
	const animation = () => {
		const cloudWidth = cloudObj.width;
		const duration = getRandomIntInclusive(15, 25);
		const tl = gsap.timeline();
		tl.fromTo(cloudObj, {x: cloudWidth}, { x: -windowWidth, ease: "none", duration: duration, repeat: -1, repeatRefresh: true});
		tl.seek(1 + Math.floor(Math.random() * duration));
		// TODO: make larger clouds slower
	}
	
	onMount(() => {
		animation();
	 });
</script>

<img bind:this={cloudObj} src={cloud} alt="cloud" class="right-0 w-48 lg:w-80" />
