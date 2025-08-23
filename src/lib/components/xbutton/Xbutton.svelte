<button
	class={`${$$props.class || ''} cursor-pointer text-3xl font-bold text-gray-700 hover:text-red-700`}
	on:click
>
	<slot />
</button>
