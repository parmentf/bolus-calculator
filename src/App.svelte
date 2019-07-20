<script>
	import BolusCalculator from './BolusCalculator.svelte';
	export let name;
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Welcome to {name}!</h1>

<BolusCalculator/>
