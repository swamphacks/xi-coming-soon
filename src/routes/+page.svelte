<script lang="ts">
	import Button from '$lib/components/button/Button.svelte';
	import Car from '$lib/components/car/Car.svelte';
	import Cloud from '$lib/components/cloud/Cloud.svelte';
	import Link from '$lib/components/link/Link.svelte';
	
	import { PUBLIC_INTEREST_URL, PUBLIC_INTEREST_SOURCE } from '$env/static/public';

	interface inputErrorType {
		error: string
		message: string
	}
	let error: inputErrorType;
	
	let showForm = $state(false);
	let inputEmail = $state("");
	let inputError = $state("");
	let inputSuccess = $state(false);
	let windowWidth = $state(0);

	const openForm = () => {
		showForm = !showForm;
	};
	
	const closeForm = () => {
		showForm = false;
		inputSuccess = false;
		inputError = "";
		inputEmail = "";
	}
	
	const closeFormWithEsc = (e: KeyboardEvent) => {
		if (e.repeat) return;
		if (!showForm) return;

		if (e.key == "Escape") {
			closeForm();
		}
	}
	
	const sendInterestRequest = async () => {
		inputSuccess = false;
		inputError = "";
		const res = await fetch(PUBLIC_INTEREST_URL, {
			method: "POST",
			headers: {
        'content-type': 'application/json'
      },
			body: JSON.stringify({email: inputEmail, source: `${PUBLIC_INTEREST_SOURCE}`})
		}).catch(()=> {
			inputError = "Could not connect to api";
		});
		if (res && res.ok) {
			inputSuccess = true;
		} else if (res && !res.ok) {
			error = await res.json();
			inputError = error.message;
		} else if (inputError !== "") {
			// Thrown on fetch failure.
			return;
		} else  {
			inputError = "An unexpected error has occured."
		}
	}
</script>

{#if showForm}
	<div class="fixed z-2 w-full h-full flex flex-col items-center justify-center">
		<div class="flex flex-col items-start">
			<div class="w-auto bg-input-group border-button-border border-2 rounded p-6">
				<Button on:click={closeForm} class="mb-3 hover:text-red-700 hover:bg-close hover:border-close-border active:bg-close-active active:border-close-active">X</Button>
				<!-- todo - x button placement -->
				<!-- form used to run subscribe button when enter key is pressed -->
				<form class="w-auto flex flex-col gap-3 justify-center items-stretch"> 
					<input
						type="email"
						bind:value={inputEmail}
						id="email-input"
						class="w-max lg:w-md rounded border-2 border-b-4 border-input-border bg-input p-4 text-xl lg:text-2xl font-bold text-input-text focus:border-input-focus-border"
						placeholder="email"
					/>
					<Button on:click={sendInterestRequest} class="w-auto text-xl lg:text-2xl">Subscribe</Button>
					{#if inputError}
						<p class="text-red-700 text-md font-bold lg:text-lg text-center">{inputError}</p>
					{/if}
					{#if inputSuccess}
						<p class="text-green-700 text-md font-bold lg:text-lg text-center">Subscribed successfully!</p>
					{/if}
				</form>
			</div>
		</div>
	</div>
	<div class="z-1 min-h-full min-w-full bg-gray-800 opacity-50"></div>
{/if}

<svelte:window bind:innerWidth={windowWidth} on:keydown={closeFormWithEsc}/>
<div class="overflow-hidden min-w-full min-h-full w-full h-full">
	<div class="absolute top-[2vh] right-0 -z-1">
		<Cloud {windowWidth} />
		<Cloud {windowWidth} />
		<Cloud {windowWidth} /> 
		<Cloud {windowWidth} /> 
	</div>
	<div class="flex min-h-screen flex-col items-center justify-center gap-3">
		<p class="title-text text-center m-4 sm:m-6 text-5xl sm:text-7xl lg:text-8xl font-bold tracking-wide text-header">Swamphacks XI<br>Coming soon</p>
		<div class="flex flex-row gap-3">
			<Button on:click={openForm} class="text-md sm:text-xl lg:text-3xl">Sign up for updates</Button>
			<Link href="https://x.swamphacks.com/recap"><Button class="text-md sm:text-xl lg:text-3xl">SH X Recap</Button></Link
			>
		</div>
		<Link href="mailto:sponsors@swamphacks.com"
			><Button class="text-sm sm:text-md lg:text-xl">Interested in becoming a sponsor?</Button></Link
		>
	</div>
	<div class="absolute left-[3vw] bottom-[1vh] -z-1">
		<Car class="w-64 lg:w-96" />
	</div>
	<div class="absolute bottom-0 min-w-full h-[2vh] bg-header -z-2"></div>
</div>
