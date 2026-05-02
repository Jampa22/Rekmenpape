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

<h2></h2>
<p></p>

<button onclick="resetAll()">P1 or P2</button>

<div id="output">Klik op een nummer</div>

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
