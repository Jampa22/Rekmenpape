<html lang="nl">
<head>
  <meta charset="UTF-8">
  <title>0-36 Uitkomst App</title>
  <style>
    body {
      font-family: Arial;
      text-align: center;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(6, 60px);
      gap: 10px;
      justify-content: center;
      margin-top: 20px;
    }

    .cell {
      width: 60px;
      height: 60px;
      background: #eee;
      border: 1px solid #999;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      font-weight: bold;
      user-select: none;
    }

    .cell:hover {
      background: #ddd;
    }

    #output {
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
    }

    button {
      margin-top: 10px;
      padding: 8px 12px;
    }
  </style>
</head>
<body>

<h2>GRS</h2>

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
    if (user === "Jampa" && Roulette === "Roulette") {
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



<div id="output">Choose the following number</div>

<div class="grid" id="grid"></div>

<script>
  const grid = document.getElementById("grid");
  const output = document.getElementById("output");

  // opgeslagen data
  let data = JSON.parse(localStorage.getItem("outcomes")) || {};

  function save() {
    localStorage.setItem("outcomes", JSON.stringify(data));
  }

  for (let i = 0; i <= 36; i++) {
    const cell = document.createElement("div");
    cell.className = "cell";
    cell.textContent = i;

    // CLICK = uitkomst tonen
    cell.addEventListener("click", () => {
      let uitkomst = data[i];

      if (!uitkomst) {
        output.textContent = "Nummer " + i + " heeft nog geen uitkomst ingesteld.";
      } else {
        output.textContent = "🎯 Nummer " + i + " → " + uitkomst;
      }
    });

    // DOUBLE CLICK = uitkomst instellen
    cell.addEventListener("dblclick", () => {
      let nieuw = prompt("Geef jouw uitkomst voor nummer " + i + ":", data[i] || "");
      if (nieuw !== null && nieuw.trim() !== "") {
        data[i] = nieuw;
        save();
        output.textContent = "✔ Uitkomst opgeslagen voor nummer " + i;
      }
    });

    grid.appendChild(cell);
  }

  function resetAll() {
    if (confirm("Alles resetten?")) {
      localStorage.removeItem("outcomes");
      location.reload();
    }
  }
</script>

</body>
</html>
