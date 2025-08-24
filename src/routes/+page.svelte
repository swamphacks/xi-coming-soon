<script lang="ts">
	import Button from '$lib/components/button/Button.svelte';
	import Car from '$lib/components/car/Car.svelte';
	import Link from '$lib/components/link/Link.svelte';
	import Xbutton from '$lib/components/xbutton/Xbutton.svelte';
	import { INTEREST_URL, SOURCE_URL } from "$env/static/private"

	let showForm = $state(false);
	let inputEmail = $state("");
	let inputError = $state("");
	let inputSuccess = $state(false);

	const toggleForm = () => {
		showForm = !showForm;
	};
	
	const sendInterestRequest = async () => {
		console.log(inputEmail);
		const res = await fetch(INTEREST_URL, {
			method: "POST",
			body: JSON.stringify({email: inputEmail, source: SOURCE_URL})
		});
		if (!res.ok) {
			inputError = await res.json();
		} else {
			inputSuccess = true;
		}
	}
</script>

{#if showForm}
	<div
		class="fixed z-2 flex h-screen min-h-full w-screen min-w-full flex-col items-center justify-center"
	>
		<div class="flex flex-row gap-3 rounded bg-input-group p-6">
			<Xbutton on:click={toggleForm} class="mr-2">X</Xbutton>
			<!-- form used to run subscribe button when enter key is pressed -->
			<form> 
				<input
					type="email"
					bind:value={inputEmail}
					id="email-input"
					class="w-md rounded border-2 border-b-4 border-input-border bg-input p-4 text-2xl font-bold text-input-text focus:border-input-focus-border"
					placeholder="email"
				/>
				<Button on:click={sendInterestRequest} class="text-2xl">Subscribe</Button>
			</form>
		</div>
		{#if inputError}
			<p class="text-red-500 text-lg">{inputError}</p>
		{/if}
		{#if inputSuccess}
			<p class="text-green-500 text-lg">Subscribed successfully.</p>
		{/if}
	</div>
	<div class="fixed z-1 min-h-full min-w-full bg-gray-800 opacity-50"></div>
{/if}

<div class="-z-1 h-screen w-screen overflow-hidden">
	<div class="flex min-h-screen flex-col items-center justify-center gap-3">
		<p class="title-text m-6 text-8xl font-bold tracking-wide text-header">Coming soon</p>
		<div class="flex flex-row gap-3">
			<Button on:click={toggleForm} class="text-3xl">Sign up for updates</Button>
			<Link href="https://x.swamphacks.com/recap"><Button class="text-3xl">SH X Recap</Button></Link
			>
		</div>
		<Link href="mailto:contact@swamphacks.com"
			><Button class="text-xl">Interested in becoming a sponsor?</Button></Link
		>
	</div>
	<div class="absolute left-1/6 bottom-[2vh] -z-1">
		<Car class="w-sm" />
	</div>
	<div class="absolute bottom-0 min-w-full h-[2vh] bg-header -z-2"></div>
</div>
