<html>
<form onsubmit="javascript:handleClick();return false">
	<label for="date">Date (MM-DD-YYY): </label>
	<input type="text" id="date" name="date"><br><br>

	<label for="calculation">Choose an option:</label>

	<select id="calculation">
		<option value="isLeapYear">Is Leap Year</option>
		<option value="dayOfYear">Day Of Year</option>
		<option value="firstDayOfYear">First Day of Year</option>
		<option value="dayOfWeek">Day of Week</option>
	</select>
	<input type="submit" value="Submit">

</form>

<p id="results"></p>

<script>
	function handleClick() {
		const date = document.getElementById("date").value;
		const dateValues = date.split("-");
		const day = dateValues[0];
		const month = dateValues[1];
		const year = dateValues[2];

		const calculationText = document.getElementById("calculation")
		const calculation = document.getElementById("calculation").value;
		console.log(calculation);

		let url = "https://womeninstem.tk/api/calendar/" + calculation;

		switch (calculation) {
			case "isLeapYear":
				url += `/${year}`;
				break;
			case "dayOfYear":
				url += `/${month}/${day}/${year}`;
				break;
				url += `/${year}`;
			case "firstDayOfYear":
				break;
			case "dayOfWeek":
				url += `/${day}/${month}/${year}`;
				break;

		}

		var requestOptions = {
			method: 'GET',
			redirect: 'follow'
		};

		fetch(url)
			.then(response => response.json())
			.then(result => document.getElementById("results").innerHTML = result)
			.catch(error => console.log('error', error));
	}
</script>

</html>