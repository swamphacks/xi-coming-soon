<script lang="ts">
    import Button from "$lib/components/button/Button.svelte";
	import Car from "$lib/components/car/Car.svelte";
	import Link from "$lib/components/link/Link.svelte";
	import Xbutton from "$lib/components/xbutton/Xbutton.svelte";
</script>

<div class="fixed h-screen w-screen min-h-full min-w-full flex flex-col justify-center items-center z-2">
    
    <div class="flex flex-row gap-3 bg-input-group p-6 rounded">
        <Xbutton class="mr-2">X</Xbutton>
        <input type="email" id="email-input" class="bg-input text-input-text w-md p-4 text-2xl font-bold border-b-4 border-2 rounded border-input-border focus:border-input-focus-border" placeholder="email">
        <Button class="text-2xl">Subscribe</Button>
    </div>
</div>
<div class="fixed bg-gray-800 opacity-50 min-h-full min-w-full z-1"></div>

<div class="h-screen w-screen overflow-hidden -z-1">
    <div class="flex flex-col min-h-screen justify-center items-center gap-3">
        <p class="text-8xl title-text tracking-wide font-bold m-6 text-header">Coming soon...</p>
        <div class="flex flex-row gap-3">
            <Button class="text-3xl">Sign up for updates</Button>
            <Link href="https://x.swamphacks.com/recap"><Button class="text-3xl">SH X Recap</Button></Link>
        </div>
        <Link href="mailto:contact@swamphacks.com"><Button class="text-xl">Interested in becoming a sponsor?</Button></Link>
    </div>
    <div class="absolute bottom-0 right-1/5">
        <Car class="w-sm" />
    </div>

</div>
