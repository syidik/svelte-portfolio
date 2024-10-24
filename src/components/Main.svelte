<script>
	import { fly } from 'svelte/transition';
    import { onMount } from 'svelte';

    let visible = false;
    let element;

    onMount(() => {
        const observer = new IntersectionObserver(
            ([entry]) => {
                if (entry.isIntersecting) {
                    visible = true; // Trigger animation
                    console.log(visible)
                    observer.disconnect(); // Stop observing after entering view
                }
            },
            { threshold: 0.1 } // Trigger when 10% of the element is visible
        );

        if (element) observer.observe(element);
  });
</script>

<section bind:this={element} class="sm:px-16 px6 absolute inset-0 top-[1020px] max-w-7xl mx-auto flex flex-col items-start gap-5">
    <div>
        {#if visible}
            <h2 in:fly={{ y:-50, duration: 1500 }} class="text-white font-black md:text-[60px] sm:text-[50px] xs:text-[40px] text-[30px]">About Me</h2>
        {/if}
    </div>
    <p class="mt-4 text-gray-400 text-[17px] max-w-3xl leading-[30px]">
        I like to learn new things, mostly working with javascript. Learning to make games in 
        my free time. Currently learning Go and really having fun with it.
    </p>
</section>