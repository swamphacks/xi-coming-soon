<button 
        class={`${$$props.class || ''} text-3xl text-gray-700 hover:text-red-700 cursor-pointer`}

        on:click
        >
        <slot/>
</button>