
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {font-family: Arial, Helvetica, sans-serif;}
form {border: 3px solid #f1f1f1;}

input[type=text], input[type=password] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

button {
  background-color: #3C4F76;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
}

button:hover {
  opacity: 0.8;
}

.cancelbtn {
  width: auto;
  padding: 10px 18px;
  background-color: #383F51;
}

.imgcontainer {
  text-align: center;
  margin: 24px 0 12px 0;
}

img.avatar {
  width: 40%;
  border-radius: 50%;
}

.container {
  padding: 16px;
}

span.psw {
  float: right;
  padding-top: 16px;
}


@media screen and (max-width: 300px) {
  span.psw {
     display: block;
     float: none;
  }
  .cancelbtn {
     width: 100%;
  }
}
</style>
</head>
<body>

<h2>Login to DN Marketplace!</h2>

<form>
  
  <div class="container" style="background-color:#DDDBEF">
    <label for="uname"><b>Email</b></label>
    <input id="email" type="text" placeholder="Enter Username" name="uname" required>

    <label for="psw"><b>Password</b></label>
    <input id="pass" type="password" placeholder="Enter Password" name="psw" required>
      
	<button onclick="authenticate()">Login</button>
	
	
    
  </div>

  <div class="container" style="background-color:#DDDBEF">
    <button type="button" class="cancelbtn">Cancel</button>
    <span class="psw"><a href="#">Don't have an account? Create one!</a></span>
  </div>
</form>

</body>

<script>

function authenticate() {
	let email = document.getElementById("email").value;
	let pass = document.getElementById("pass").value;
	
	console.log("hello");
	//setTimeout(() => {  console.log("World!"); }, 100000);
	var myHeaders = new Headers();
	myHeaders.append("Content-Type", "application/json");
	myHeaders.append("Cookie", "jwt=eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJtZWVuYUB0ZXN0LmNvbSIsImV4cCI6MTY3NTY2ODUyOSwiaWF0IjoxNjc1NjUwNTI5fQ.birnz8HE9yIbLqxQFeFbAYV649NdHU_D9ViZxjNCg6dZB2rkcM4AdSjXBjI0pGvVEoIGispDLGrYj6VWQwkkiw");
	var raw = JSON.stringify({
  "email": email,
  "password": pass
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};
 console.log("hello");
fetch("https://marketplace.nighthawkcodingsociety.com/authenticate", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
  
 }
 console.log("hello");
 

</script>
</html>
