<script>
	import CRUD from './CRUD.svelte';
	import { set_prerendering } from '__sveltekit/environment';
	import Counter from './counter.svelte';
	import FlightBooker from './flightBooker.svelte';
	import TempretureConverter from './TempretureConverter.svelte';
	import Timer from './timer.svelte';

	const guiExampleTitles = [
		'Counter',
		'Temperature Converter',
		'Flight Booker',
		'Timer',
		'CRUD',
		'Circle Drawer',
		'Cells'
	];

	const guiExamples = [Counter, TempretureConverter, FlightBooker, Timer, CRUD];
	let selectedGuiIndex = $state(0);

	let SelectedGUI = $derived(guiExamples[selectedGuiIndex]);
</script>

<main>
	<div class="sideMenu">
		<div class="topPart">
			<p>7 GUIs</p>
			<div class="svelteLogo">
				<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 102.25 122.88"
					><defs
						><style>
							.a {
								fill: #ff3e00;
							}
							.b {
								fill: #fff;
							}
						</style></defs
					><title>svelte</title><path
						class="a"
						d="M95.73,16.26C84.32-.07,61.78-4.91,45.49,5.47L16.87,23.71A32.83,32.83,0,0,0,2,45.69a35.13,35.13,0,0,0-.55,6.14,34.69,34.69,0,0,0,4,16.06A33,33,0,0,0,.54,80.16a35,35,0,0,0,6,26.46c11.41,16.33,34,21.17,50.24,10.79L85.37,99.17a32.76,32.76,0,0,0,14.83-22,34.08,34.08,0,0,0,.55-6.13A34.72,34.72,0,0,0,96.8,55a33,33,0,0,0,4.91-12.26,36,36,0,0,0,.54-6.13,34.93,34.93,0,0,0-6.52-20.33Zm0,0Z"
					/><path
						class="b"
						d="M42.69,108.16a22.94,22.94,0,0,1-5.72.73A22.7,22.7,0,0,1,18.3,99.11a21,21,0,0,1-3.92-12.23,21.6,21.6,0,0,1,.32-3.68,20.52,20.52,0,0,1,.69-2.67l.54-1.64L17.39,80a37.13,37.13,0,0,0,11.2,5.6l1.06.32-.1,1.06c0,.18,0,.37,0,.55a6.36,6.36,0,0,0,1.18,3.7,6.82,6.82,0,0,0,5.62,3,6.65,6.65,0,0,0,1.72-.22,6.28,6.28,0,0,0,1.76-.77L68.42,74.91a6,6,0,0,0,2.79-5.09A6.35,6.35,0,0,0,70,66.13a6.85,6.85,0,0,0-5.63-2.94,6.65,6.65,0,0,0-1.72.22,6,6,0,0,0-1.75.77L50,71.14a21.06,21.06,0,0,1-5.81,2.55,23.06,23.06,0,0,1-5.72.73A22.73,22.73,0,0,1,19.8,64.65a21.05,21.05,0,0,1-3.92-12.23,21.6,21.6,0,0,1,.32-3.68,19.82,19.82,0,0,1,8.92-13.23L53.74,17.28a21,21,0,0,1,5.81-2.56A23,23,0,0,1,65.27,14,22.74,22.74,0,0,1,84,23.76,21.05,21.05,0,0,1,87.87,36a21.72,21.72,0,0,1-.32,3.69,20.52,20.52,0,0,1-.69,2.67L86.32,44l-1.46-1.07a36.9,36.9,0,0,0-11.2-5.6L72.6,37l.1-1.06c0-.18,0-.37,0-.55a6.42,6.42,0,0,0-1.18-3.71,6.85,6.85,0,0,0-5.62-2.94A6.65,6.65,0,0,0,64.2,29a5.89,5.89,0,0,0-1.76.77L33.82,48a6,6,0,0,0-2.69,4A6.92,6.92,0,0,0,31,53.06a6.35,6.35,0,0,0,1.18,3.69,6.84,6.84,0,0,0,5.62,2.94,6.65,6.65,0,0,0,1.72-.22,6,6,0,0,0,1.76-.77l10.92-7a20.93,20.93,0,0,1,5.81-2.55,23,23,0,0,1,5.72-.73,22.74,22.74,0,0,1,18.68,9.77,21.05,21.05,0,0,1,3.92,12.23A20.64,20.64,0,0,1,86,74.14a19.78,19.78,0,0,1-8.92,13.23L48.51,105.6a21,21,0,0,1-5.82,2.56Zm0,0Z"
					/></svg
				>
			</div>
		</div>

		<div class="navigationMenu">
			{#each guiExampleTitles as gui, i}
				{@render selectionButton(i, gui)}
			{/each}
		</div>
	</div>
	<div class="guiPreview">
		<p>{guiExampleTitles[selectedGuiIndex]}</p>
		<SelectedGUI />
	</div>
</main>

{#snippet selectionButton(i, title)}
	<button class="selectionButton" onclick={(selectedGuiIndex = i)}>
		<p style="margin-right: 15px; color: {selectedGuiIndex === i ? '#ff3e00' : ''}">
			{i + 1}.
		</p>
		<p style="color: {selectedGuiIndex === i ? '#ff3e00' : ''}">{title}</p>
	</button>
{/snippet}

<style>
	:global(*) {
		font-family: Manrope;
		color: #d2d6e0;
		padding: 0;
		margin: 0;
	}

	.guiPreview {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 80%;
		height: 100%;
		flex-direction: column;
		gap: 20px;

		p {
			font-size: 40px;
			font-weight: bold;
		}
	}

	.sideMenu {
		background-color: #19191f;
		width: 20%;
		height: 100%;
		border-width: 0px 1px 0px 0px;
		border-color: #3a3b3d;
		border-style: solid;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	.topPart {
		width: 100%;
		text-align: center;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		height: 20%;
		border-width: 0px 0px 1px 0px;
		border-color: #3a3b3d;
		border-style: solid;
	}

	.topPart p {
		font-size: 55px;
		width: 170px;
		margin-right: 10px;
		text-align: center;
		font-weight: bold;
	}

	.navigationMenu {
		height: 80%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		gap: 5px;
	}

	.svelteLogo {
		width: 60px;
		margin-top: 10px;
	}

	main {
		width: 100%;
		height: 100vh;
		background-color: #16171d;
		display: flex;
		flex-direction: row;
		gap: 10px;
		align-items: center;
	}

	.selectionButton {
		height: 70px;
		display: flex;
		justify-content: left;
		align-items: center;
		font-size: 19px;
		font-weight: bold;
		background-color: transparent;
		border: none;
		padding-left: 30px;
		text-align: left;
		cursor: pointer;
	}

	.selectionButton:hover p {
		color: rgb(250, 98, 47);
	}

	.selectionButton:active p {
		color: #ff3e00;
	}
</style>
