<button 
        class={`${$$props.class || ''} bg-button hover:bg-button-hover active:bg-button-active text-button-text font-bold py-2 px-4 border-b-4 border-button-border active:border-button-active-border active:text-button-active-text rounded cursor-pointer`}

        on:click
        >
        <slot/>
</button>