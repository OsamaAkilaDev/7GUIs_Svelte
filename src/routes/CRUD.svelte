<script>
</script>

<main>
	<div class="topPart">
		<div class="topLeftPart">
			<div class="filterContainer">
				<p>Filter prefix:</p>
				<input />
			</div>

			<select size="5">
				<option class="option">Testing the display</option>
				<option class="option">Testing the display</option>
				<option class="option">Testing the display</option>
				<option class="option">Testing the display</option>
			</select>
		</div>
		<div class="topRightPart">
			<div class="nameFieldContainer">
				<p>Name:</p>
				<input />
			</div>
			<div class="nameFieldContainer">
				<p>Surname:</p>
				<input />
			</div>
		</div>
	</div>
	<div class="bottomPart"></div>
</main>

<style>
	* {
		outline: none;
		font-size: 17px;
	}

	input {
		background-color: #cecece;
		border: none;
		color: black;
		padding: 3px 7px 3px 7px;
		border-radius: 5px;
	}

	main {
		width: 500px;
		height: 300px;
		border-radius: 15px;
		background-color: #32323d;
		display: grid;
		grid-template-rows: repeat(6, 16.6666666667%);
		padding: 20px;
		box-sizing: border-box;
	}

	.topPart {
		grid-row: 1/6;
		display: grid;
		grid-template-columns: repeat(2, 50%);
	}

	.bottomPart {
		grid-row: 6/7;
	}

	.topLeftPart {
		display: flex;
		flex-direction: column;
	}

	.topRightPart {
		display: flex;
		flex-direction: column;
		margin-left: 10px;
		justify-content: center;
	}

	.filterContainer {
		display: grid;
		grid-template-columns: 45% 55%;
		margin-bottom: 10px;
	}

	.nameFieldContainer {
		display: grid;
		margin-bottom: 10px;
	}

	select {
		background-color: #484f5a;
		border: none;
		overflow-y: auto;
		height: 100%;
		padding: 8px;
		border-radius: 8px;
	}

	.option {
		color: black;
		border-radius: 5px;
		padding: 3px 7px 3px 7px;
		box-sizing: border-box;
		margin-bottom: 4px;
	}
</style>
