<script lang="ts">
	import { onMount } from "svelte";
	import gsap from "gsap";
	import cloud from '$lib/assets/cloud.png';

	let cloudObj: HTMLImageElement;
    // let { clientWidth } = $props();

	// onMount(async () => {
        // const xTranslate = -clientWidth - 100;
	    // const tl = gsap.timeline({ repeat: -1, repeatDelay: 1, repeatRefresh: true });
	    // tl.to(cloudObj, { x: xTranslate, delay: 1 })
		;
	// });
</script>

<img bind:this={cloudObj} src={cloud} alt="car" class={`${$$props().class || ''}`} />
