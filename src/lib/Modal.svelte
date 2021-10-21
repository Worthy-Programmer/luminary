
<script>
import { createEventDispatcher } from 'svelte';

    import {fade} from 'svelte/transition';
    import chevronUp from "/static/img/icons/chevron-up.svg";

    export let containerProps = {}
    const dispatch = createEventDispatcher()
</script>

<section transition:fade  class="container" {...containerProps}>
    <img src={chevronUp} alt="Close Modal" on:click={() => dispatch('close')}>
        <slot />
</section>

<style>
    section {
        position: fixed;
        left: 50%;
        top: 50%;
        transform: translateX(-50%) translateY(-50%);

        background-color: white;

        border-radius: 25px;
        box-shadow: 0px 10px 10px var(--modal-box-shadow, #00000029);
        border: var(--modal-border, 2px solid var(--light-gray));
        
        /* padding: 30px; */
        box-sizing: border-box;
                padding: var(--modal-padding,50px);

    }


    img {
        float:right;
        width: 20px;
    }


</style>