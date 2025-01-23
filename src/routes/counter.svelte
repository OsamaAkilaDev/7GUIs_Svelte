<script>
	let count = $state(0);
	let { incrementValue = 1 } = $props();
</script>

<main>
	<input type="text" bind:value={count} readonly />
	<button onclick={() => (count += incrementValue)}>Count</button>
</main>

<style>
	* {
		font-size: 16px;
	}

	main {
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 5px;
	}

	input {
		background-color: #484f5a;
		border: none;
		color: #d2d6e0;
		width: 200px;
		height: 40px;
		border-radius: 4px;
		padding-left: 12px;
		padding-top: 4px;
		box-sizing: border-box;
		cursor: default;
	}

	input:focus,
	button:focus {
		outline: none;
	}

	button {
		background-color: #484f5a;
		border: none;
		color: #d2d6e0;
		width: 70px;
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
