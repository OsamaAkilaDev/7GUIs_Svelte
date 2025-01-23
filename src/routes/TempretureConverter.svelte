<script>
	class Tempreture {
		#c = $state(0);
		#f = $state(0);

		get c() {
			return this.#c;
		}

		set c(c) {
			this.#c = c;
			this.#f = c * (9 / 5) + 32;
		}

		get f() {
			return this.#f;
		}

		set f(f) {
			this.#f = f;
			this.#c = (f - 32) * (5 / 9);
		}
	}

	const tempreture = new Tempreture();
</script>

<main>
	<input type="number" bind:value={tempreture.c} />
	<div>Celsius =</div>
	<input type="number" bind:value={tempreture.f} />
	<div>Fehrenheit</div>
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

	input:focus {
		outline: none;
	}

	div {
		color: #d2d6e0;
		font-family: Arial, Helvetica, sans-serif;
	}

	input[type='number']::-webkit-inner-spin-button {
		-webkit-appearance: none;
	}
</style>
