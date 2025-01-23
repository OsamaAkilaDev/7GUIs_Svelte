<script>
	import dayjs from 'dayjs';
	let selected = $state('oneWay');

	let flightDate = $state('');
	let returningFlightDate = $state('');

	let flightDayjs = $derived(dayjs(flightDate));
	let returnDayjs = $derived(dayjs(returningFlightDate));

	function formatDate(dateDayjs) {
		return dateDayjs.format('D/M/YYYY');
	}

	function checkValidity() {
		if (selected === 'oneWay' && !flightDate) return false;
		else if (selected === 'return' && (!flightDate || !returningFlightDate)) return false;
		else return true;
	}

	function handleSubmit(e) {
		e.preventDefault();
		alert(
			`Your flight is booked on the ${formatDate(flightDayjs)}. ${selected === 'return' ? `, and the returning flight is booked on ${formatDate(returnDayjs)}` : ''}`
		);
	}
</script>

<form onsubmit={handleSubmit}>
	<select bind:value={selected}>
		<option value="oneWay">One way flight</option>
		<option value="return">Return flight</option>
	</select>

	<label>
		<p>Flight Date</p>
		<input type="date" bind:value={flightDate} />
	</label>

	<label>
		<p>Return Date</p>
		<input type="date" bind:value={returningFlightDate} disabled={selected === 'oneWay'} />
	</label>

	<input
		type="submit"
		value="Book"
		disabled={(selected === 'oneWay' && !flightDate) ||
			(selected === 'return' && (!flightDate || !returningFlightDate)) ||
			flightDayjs.isAfter(returningFlightDate)}
	/>
</form>

<style>
	form {
		width: 250px;
		display: flex;
		flex-direction: column;
		gap: 5px;
	}

	label {
		display: flex;
		align-items: center;
	}

	label p {
		width: 40%;
		color: #d2d6e0;
		font-family: Arial, Helvetica, sans-serif;
		margin: 0;
	}

	label input {
		width: 60%;
	}

	select,
	input {
		background-color: #484f5a;
		border: none;
		color: #d2d6e0;
		height: 40px;
		border-radius: 4px;
		padding-left: 9px;
		padding-top: 2px;
		box-sizing: border-box;
		cursor: default;
		font-size: 16px;
	}

	select:focus,
	input:focus {
		outline: none;
	}

	input[type='submit']:hover {
		background-color: #3b4049;
	}

	input[type='submit']:active {
		background-color: #2e333a;
	}

	input[type='submit']:disabled {
		background-color: #434446;
		cursor: not-allowed;
	}
</style>
