<script lang="ts">
	let timer = 0;
	let interval: number | null = null;

	function startChronometer() {
		interval = setInterval(() => {
			timer++;
		}, 1000);
	}

	function stopChronometer() {
		clearInterval(interval as number);
	}

	function resetChronometer() {
		timer = 0;
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Timer SvelteKit App" />
</svelte:head>

<section>
	<h1>Timer</h1>
	<p>{timer}</p>
	<button on:click={startChronometer}>Start</button>
	<button on:click={stopChronometer}>Stop</button>
	<button on:click={resetChronometer}>Reset</button>
</section>

<style>
</style>
