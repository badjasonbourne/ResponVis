<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
  
    export let open = false;
    export let w = "200px";
    export let desc = "I recommend you to change the view";
    let views = ["ChoroplethMap", "Hexmap", "WaffleChart", "WaffleChart"];
    export let display;
  
    let width;
    $: width = w.toString() + "px";

    function closeModal() {
        open = false;
        dispatch('close');
    }

    function confirmModal() {
        open = false;
        dispatch('confirm');
    }

</script>
  
{#if open}
<div class="modal" style="width: {width}">
    <p>{desc}, I recommend that you switch to {views[display]}</p>
    <div class="modal-operation">
        <button on:click={confirmModal}>Switch to {views[display]}</button>
        <button on:click={closeModal}>Keep the current view</button>
    </div>
</div>
{/if}

<style>
.modal {
    border: 1px solid black;
    padding: 12px;
    background: white;
    border-radius: 5px;
}

.modal-operation {
    display: flex;
    margin-top: 16px;
    gap: 12px;
}

p {
    font-size: 14px;
}
</style>