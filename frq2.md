
<html>
<style>
#grad {
        height: 500px;
        background-color: blue;
        background-image: linear-gradient(to right, #f0fff7,  	#b3c6ff);
      }
body {
        background-color: #F0F8FF;
        color: black;
      }
      h2 {
        background-color: #F0F8FF;
        color: black;
      }
      p {
        background-color: #ffffcc;
        color: black;
      }
      h1 {
        color: black;
      }
</style>
<body style="background-color:#F0F8FF;">
<div id="grad">
<h1>Welcome to Step Tracker</h1>
<p style="background-color:#b3c6ff;">Enter your id to view your step tracker info (Example try ID of 19)</p>

<form id="frm1" action="/action_page.php">
  ID: <input type="text" id="person_id" name="person_id"><br>
  <input type="button" onclick="getStepInfo()" value="Submit">
</form>
<p id = "email"></p>
<p id = "password"></p>
<p id = "name"></p>
<p id = "dob"></p>
<p id = "height"></p>
<p id = "weight"></p>
<p id = "totalSteps"></p>
<p id = "age"></p>
<p id = "goalSteps"></p>

<p style="background-color:#b3c6ff;">Enter your id to view your active days</p>
<form id="frm2" action="/action_page.php">
  ID: <input type="text" id="person_id" name="person_id"><br>
  <input type="button" onclick="getActiveDays()" value="Submit">
</form>
<p id = "active_days"></p>

<p style="background-color:#b3c6ff;">Enter your id to view your average steps</p>
<form id="frm3" action="/action_page.php">
  ID: <input type="text" id="person_id" name="person_id"><br>
  <input type="button" onclick="getAverageSteps()" value="Submit">
</form>
<p id = "average_steps"></p>

<p style="background-color:#b3c6ff;">Enter your id to view your average mood</p>
<form id="frm3" action="/action_page.php">
  ID: <input type="text" id="person_id" name="person_id"><br>
  <input type="button" onclick="getAverageMood()" value="Submit">
</form>
<p id = "average_mood"></p>

<p style="background-color:#b3c6ff;">Enter your id to check if you have been active</p>
<form id="frm4" action="/action_page.php">
  ID: <input type="text" id="person_id" name="person_id"><br>
  <input type="button" onclick="getActiveCheck()" value="Submit">
</form>
<p id = "average_check"></p>


<script>

function getStepInfo() {
  const person_id = document.getElementById("person_id").value;
  const url = 'https://womeninstem.tk/api/person/' + person_id;
  console.log(person_id);
  console.log(url);
  
  fetch(url)
    .then((response) => {
      response.json().then(info => {
	  console.log(info.userId);
		document.getElementById("email").innerHTML = "Email: " + info.email;
		document.getElementById("password").innerHTML = "Password: " + info.password;
		document.getElementById("name").innerHTML = "Name: " + info.name;
		document.getElementById("dob").innerHTML = "dob: " + info.dob;
		document.getElementById("height").innerHTML = "Height: " + info.height;
		document.getElementById("weight").innerHTML = "Weight: " + info.weight;
		document.getElementById("totalSteps").innerHTML = "Total Steps: " + info.totalSteps;
		document.getElementById("age").innerHTML = "Age: " + info.age;
		document.getElementById("goalSteps").innerHTML = "Goal Steps: " + info.goalSteps;
	  });
    })
  
    .catch(function(error) {
      console.log(error);
    });
}

function getActiveDays() {
  const person_id2 = document.getElementById("person_id2").value;
  const url = 'https://womeninstem.tk/api/steps/stepsInfo/' + person_id2;
  fetch(url)
    .then((response) => {
      response.json().then(info => {
		document.getElementById("active_days").innerHTML = "Active Days: " + info.activeDays;
	  
	  	  });
    })
  
    .catch(function(error) {
      console.log(error);
    });
}
  

function getAverageSteps() {
  const person_id3 = document.getElementById("person_id3").value;
  const url = 'https://womeninstem.tk/api/steps/stepsInfo/' + person_id3;
  console.log(document.getElementById("person_id").value);
  fetch(url)
    .then((response) => {
      response.json().then(info => {
		document.getElementById("average_steps").innerHTML = "Average Steps: " + info.averageSteps;
	  
	  	  });
    })
  
    .catch(function(error) {
      console.log(error);
    });
	 
   
}

function getAverageMood() {
  const person_id4 = document.getElementById("person_id4").value;
  const url = 'https://womeninstem.tk/api/steps/stepsInfo/'+ person_id4;
  fetch(url)
    .then((response) => {
      response.json().then(info => {
		document.getElementById("average_mood").innerHTML = "Average Mood: " + info.averageMood;

	  	  });
    })
  
    .catch(function(error) {
      console.log(error);
    });
	 
	  
		
	 
   
}

function getActiveCheck() {
  const person_id5 = document.getElementById("person_id5").value; 
   const url = 'https://womeninstem.tk/api/steps/stepsInfo/'+ person_id5;
  fetch(url)
    .then((response) => {
      response.json().then(info => {
		document.getElementById("average_check").innerHTML = "Active Check: " + info.activeCheck;

	  	  });
    })
  
    .catch(function(error) {
      console.log(error);
    });
	  
		
	 
   
}
</script>
</div>
</body>
</html>