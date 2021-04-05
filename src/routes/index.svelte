<script lang="ts">
	import HealthCardScanner from '$lib/HealthCardScanner.svelte';
	export let scanning = true;

</script>

<main>
	{#if scanning}
	<HealthCardScanner on:scanned={(v) => {
		console.log("Scanned", v)
		scanning = false;
	}}
	instructionClass="scanner-instruction"
	 buttonClass="inc-button" videoClass="scanner-video" on:start-scan={() => {scanning = !scanning}}/>

	{/if}

</main>

<style>
	:global html, :global body, :global #svelte {
		height: 100%;
		margin: 0px;
		border: 0px;
		padding: 0px;
	}

	:global .scanner-video {
		grid-row: 2/3;
		grid-column: 2/3;
		object-fit: cover;
		width: min(100vmin, 100%);
		height: min(100vh, 100%);
		border-radius: 10vmin;
		justify-self: center;
	}


	:global .inc-button {
		grid-row: 3/4;
		grid-column: 2/3;
		margin-top: 1em;
		width: 100% !important;
	}

	main {
		text-align: center;
		display: grid;
		margin: 0px;
		box-sizing: border-box;
		grid-template-rows: 20vh auto 15vh;
		grid-template-columns: 2em auto 2em;
		height: 100%;
	}

	:global .scanner-instruction {
		color: #ff3e00;
		white-space: nowrap;
		text-transform: uppercase;
		font-size: 4vh;
		align-self: center;
		justify-self: center;
		overflow: hidden;
		margin: 0px;
		font-weight: 1000;
		width: 100%;
		line-height: 1.1;
		max-width: 14rem;
		grid-row: 1 / 2;
		grid-column: 1/4;
		font-family: Arial, Helvetica, sans-serif;
		
	}


</style>
