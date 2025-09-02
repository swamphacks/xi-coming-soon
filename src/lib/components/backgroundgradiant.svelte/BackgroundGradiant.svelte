<script lang="ts">
	import { onMount } from "svelte";

    const { time } = $props();
    let currentClass = $state("");

    onMount(()=>{
        const hour = time.getHours();
        const classPrefix = "absolute -z-3 h-full w-full "

        if (hour >= 6 && hour < 12) {
            currentClass = classPrefix + "bg-linear-to-b from-tod-morning-0 to-tod-morning-1"
        } else if (hour >= 12 && hour < 18) {
            currentClass = classPrefix + "bg-linear-to-b from-tod-afternoon-0 to-tod-afternoon-1"
        } else if (hour >= 18 && hour < 22) {
            currentClass = classPrefix + "bg-linear-to-b from-tod-evening-0 to-tod-evening-1"
        } else {
            currentClass = classPrefix + "bg-linear-to-b from-tod-night-0 to-tod-night-1"
        }
    });
</script>

<div class="{currentClass}"></div>