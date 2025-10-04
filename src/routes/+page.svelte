<script lang="ts">
	import Keypad from "./components/keypad.svelte"
	let target
	let keypad: Keypad
</script>


<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
	
</svelte:head>

<section>
	<div id="mainBody" class=" w-full md:w-[60%] bg-secondary">
		<math-field bind:this={target} class=" bg-[var(--secondary)] w-full " data-gramm='false'></math-field>
		<Keypad target={target} bind:this={keypad}></Keypad>
		<button on:click={() => {keypad.gridLayout = ""}}>Brick</button>
	</div>
</section>

<style>
	
</style>
