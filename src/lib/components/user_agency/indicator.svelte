<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    // 3 status: match, medium, mismatch
    export let status = "match";

    let buttonColor;
    $: buttonColor = status === "match" ? "green" : status === "medium" ? "orange" : "red";

    function handleClick() {
        dispatch("indicator-clicked");
    }
</script>

<button class="round-button" style:background-color={buttonColor} on:click={handleClick}></button>

<style>
    .round-button {
      width: 20px;
      height: 20px;
      margin-top: 10px;
      margin-left: 20px;
      border-radius: 50%;
    }
</style>