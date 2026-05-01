<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8">
  <title>Login</title>
  <style>
    body {
      font-family: Arial;
      text-align: center;
      margin-top: 100px;
      background: #f2f2f2;
    }

    .box {
      background: white;
      padding: 20px;
      width: 300px;
      margin: auto;
      border-radius: 10px;
    }

    input, button {
      width: 90%;
      padding: 10px;
      margin: 10px 0;
    }

    button {
      background: black;
      color: white;
      border: none;
      cursor: pointer;
    }

    #msg {
      margin-top: 10px;
      font-weight: bold;
    }
  </style>
</head>
<body>

<div class="box">
  <h2>🔐 Login</h2>

  <input type="text" id="username" placeholder="Gebruikersnaam">
  <input type="password" id="password" placeholder="Wachtwoord">

  <button onclick="login()">Inloggen</button>

  <div id="msg"></div>
</div>

<script>
  function login() {
    let user = document.getElementById("username").value;
    let pass = document.getElementById("password").value;

    // simpele check (demo)
    if (user === "Jampa" && pass === "Roulette") {
      document.getElementById("msg").style.color = "green";
      document.getElementById("msg").innerText = "Succesvol ingelogd! ✅";
    } else {
      document.getElementById("msg").style.color = "red";
      document.getElementById("msg").innerText = "Fout wachtwoord ❌";
    }
  }
</script>

</body>
</html>
