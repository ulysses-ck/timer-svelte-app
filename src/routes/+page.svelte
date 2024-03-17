<script lang="ts">
	// timer
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

	// timeout
	let seconds = 0;
	let minutes = 0;
	let hours = 0;
	let isFinished = false;
	let isStarted = false;

	function startTimeout() {
		isStarted = true;
		const timeTotal = hours * 3600 + minutes * 60 + seconds;

		// timeout
		setTimeout(() => {
			isFinished = true;
			isStarted = false;
		}, timeTotal * 1000);

		// interval
		const interval = setInterval(() => {
			if (seconds > 0) {
				seconds--;
			} else if (minutes > 0) {
				minutes--;
				seconds = 59;
			} else if (hours > 0) {
				hours--;
				minutes = 59;
				seconds = 59;
			} else {
				clearInterval(interval);
			}
		}, 1000);
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

	<h2>Timeout</h2>
	<p>Seconds: {seconds}</p>
	<p>Minutes: {minutes}</p>
	<p>Hours: {hours}</p>
	<label for="seconds">
		<span>Seconds:</span>
		<input type="number" bind:value={seconds} name="seconds" id="seconds" disabled={isStarted} />
	</label>
	<label for="minutes">
		<span>Minutes:</span>
		<input type="number" bind:value={minutes} name="minutes" id="minutes" disabled={isStarted} />
	</label>
	<label for="hours">
		<span>Hours:</span>
		<input type="number" bind:value={hours} name="hours" id="hours" disabled={isStarted} />
	</label>
	<button on:click={startTimeout}>Start Timeout</button>
</section>

<style>
</style>
