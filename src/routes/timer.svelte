<script>
	let duration = $state(0);
	let elapsed = $state(0);

	let interval;

	function start() {
		interval = setInterval(() => {
			elapsed += 0.1;
			if (elapsed > duration) {
				elapsed = duration;
				clearInterval(interval);
			}
		}, 100);
	}

	function reset() {
		elapsed = 0;
		start();
	}

	$effect(() => {
		if (!duration) return;
		start();
		return () => clearInterval(interval);
	});
</script>

<main>
	<div class="elapsed">
		<p>Elapsed Time: {elapsed.toFixed(1)}s</p>
		<progress id="timerProgress" value={elapsed} max={duration}></progress>
	</div>

	<div class="elapsed">
		<input type="range" bind:value={duration} min="1" max="20" />
		<p>{duration}</p>
	</div>

	<button onclick={(elapsed = 0)}>Reset</button>
</main>

<style>
	* {
		font-size: 16px;
		font-family: Arial, Helvetica, sans-serif;
		color: #d2d6e0;
	}

	main {
		display: flex;
		flex-direction: column;
		width: 330px;
	}

	.elapsed {
		display: flex;
		align-items: center;
		gap: 10px;
		justify-content: space-between;
	}

	input[type='range'] {
		width: 90%;
	}

	button {
		background-color: #484f5a;
		border: none;
		color: #d2d6e0;
		height: 40px;
		border-radius: 4px;
		text-align: center;
		padding-top: 4px;
		box-sizing: border-box;
		cursor: pointer;
	}

	button:hover {
		background-color: #3b4049;
	}

	button:active {
		background-color: #2e333a;
	}
</style>
