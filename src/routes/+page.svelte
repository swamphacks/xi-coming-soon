<script lang="ts">
	import Button from '$lib/components/button/Button.svelte';
	import Car from '$lib/components/car/Car.svelte';
	import Link from '$lib/components/link/Link.svelte';
	import Xbutton from '$lib/components/xbutton/Xbutton.svelte';

	interface inputErrorType {
		error: string
		message: string
	}
	let error: inputErrorType;
	
	let showForm = $state(false);
	let inputEmail = $state("");
	let inputError = $state("");
	let inputSuccess = $state(false);

	const toggleForm = () => {
		showForm = !showForm;
	};
	
	const sendInterestRequest = async () => {
		inputSuccess = false;
		inputError = "";
		
		// TODO: Change link to prod site
		const res = await fetch("http://localhost:8080/events/368dd49d-fc69-444f-9f0e-d2ae75db95bb/interest", {
			method: "POST",
			body: JSON.stringify({email: inputEmail, source: "Coming Soon Page"})
		});
		if (!res.ok) {
			error = await res.json();
			inputError = error.message;
		} else {
			inputSuccess = true;
		}
	}
</script>

{#if showForm}
	<div
		class="fixed z-2 flex h-screen min-h-full w-screen min-w-full flex-col items-center justify-center"
	>
		<div class="flex flex-col justify-center bg-input-group">
			<div class="flex flex-row gap-3 rounded p-6">
				<Xbutton on:click={toggleForm} onWindowKeyDown={toggleForm} class="mr-2">X</Xbutton>
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
				<p class="text-red-500 text-lg text-center mb-2">{inputError}</p>
			{/if}
			{#if inputSuccess}
				<p class="text-green-500 text-lg text-center mb-2">Subscribed successfully.</p>
			{/if}

		</div>
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
