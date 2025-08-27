<button
	class={`${$$props.class || ''} cursor-pointer rounded border-2 border-b-6 border-button-border bg-button px-4 py-2 font-bold text-button-text hover:bg-button-hover active:border-button-active active:bg-button-active active:text-button-active-text`}
	on:click
>
	<slot />
</button>
