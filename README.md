<html lang="nl">
<head>
<meta charset="UTF-8">
<title>GRS TOOL</title>

<style>
body {
  font-family: Arial;
  text-align: center;
  background: #050505;
  color: white;
}

/* STATIC glow casino background */
body::before {
  content: "";
  position: fixed;
  inset: 0;
  background:
    radial-gradient(circle at 20% 25%, rgba(0,255,200,0.15), transparent 40%),
    radial-gradient(circle at 80% 20%, rgba(255,215,0,0.12), transparent 40%),
    radial-gradient(circle at 40% 70%, rgba(0,150,255,0.10), transparent 45%),
    radial-gradient(circle at 70% 60%, rgba(255,0,150,0.08), transparent 45%);
  pointer-events: none;
}

/* title */
h2 {
  margin-top: 20px;
  text-shadow: 0 0 10px #00f2ff;
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
  background: #111;
  border: 1px solid #00f2ff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  font-weight: bold;
  user-select: none;
  box-shadow: 0 0 8px #00f2ff;
  color: white;
}

.cell:hover {
  box-shadow: 0 0 15px #00ffcc;
}

#output {
  margin-top: 20px;
  font-size: 18px;
  font-weight: bold;
  padding: 10px;
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  background: #111;
  border-radius: 10px;
  box-shadow: 0 0 12px #00f2ff;
}

button {
  margin-top: 10px;
  padding: 8px 12px;
  border: none;
  cursor: pointer;
  font-weight: bold;
  background: #00f2ff;
  border-radius: 6px;
}

button:hover {
  box-shadow: 0 0 15px #8a2be2;
}
</style>
</head>

<body>

<div id="output">Choose following number</div>

<div class="grid" id="grid"></div>

<script>
const grid = document.getElementById("grid");
const output = document.getElementById("output");

let data = JSON.parse(localStorage.getItem("outcomes")) || {};

function save() {
  localStorage.setItem("outcomes", JSON.stringify(data));
}

for (let i = 0; i <= 36; i++) {
  const cell = document.createElement("div");
  cell.className = "cell";
  cell.textContent = i;

  // klik = tonen
  cell.addEventListener("click", () => {
    if (!data[i]) {
      output.textContent = "Number" + i + " heeft nog geen uitkomst ingesteld.";
    } else {
      output.textContent = "🎯 Number " + i + " → " + data[i];
    }
  });

  // dubbelklik = instellen
  cell.addEventListener("dblclick", () => {
    let nieuw = prompt("Geef jouw uitkomst voor nummer " + i + ":", data[i] || "");
    if (nieuw && nieuw.trim() !== "") {
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

<html lang="nl">
<head>
<meta charset="UTF-8">
<title>Week Overzicht</title>

<style>
body {
  background: #000;
  color: white;
  font-family: Arial;
  padding: 20px;
}

h2 {
  text-align: center;
  color: white;
  text-shadow: 0 0 10px #00ffd5;
}

table {
  width: 100%;
  max-width: 800px;
  margin: auto;
  border-collapse: collapse;
  background: #000;
  box-shadow: 0 0 20px #00ffd5;
}

th, td {
  border: 1px solid #222;
  padding: 10px;
  text-align: center;
  background: #000;
  color: white;
}

th {
  color: #00ffd5;
  text-shadow: 0 0 6px #00ffd5;
}

input {
  width: 110px;
  padding: 6px;
  background: #000;
  border: 1px solid #333;
  color: white;
  text-align: center;
  outline: none;
}

input:focus {
  box-shadow: 0 0 10px #00ffd5;
  border-color: #00ffd5;
}

.glow {
  color: white;
  text-shadow: 0 0 8px #00ffd5;
  font-weight: bold;
}

.buttons {
  text-align: center;
  margin-top: 15px;
}

button {
  padding: 10px 18px;
  margin: 5px;
  background: #000;
  color: white;
  border: 1px solid #00ffd5;
  cursor: pointer;
  font-weight: bold;
}

button:hover {
  box-shadow: 0 0 15px #00ffd5;
}
</style>
</head>

<body>

<h2>🔥 Week Overzicht 🔥</h2>

<table>
<thead>
<tr>
  <th>Dag</th>
  <th>Inzet</th>
  <th>Winst</th>
  <th>Resultaat</th>
</tr>
</thead>

<tbody id="rows"></tbody>

<tfoot>
<tr>
  <td class="glow">Totaal</td>
  <td id="totalStake" class="glow">0</td>
  <td id="totalProfit" class="glow">0</td>
  <td id="totalResult" class="glow">0</td>
</tr>
</tfoot>
</table>

<div class="buttons">
  <button onclick="save()">💾 Opslaan</button>
  <button onclick="reset()">🔄 Reset</button>
</div>

<script>
const days = ["Maandag","Dinsdag","Woensdag","Donderdag","Vrijdag","Zaterdag","Zondag"];

const rows = document.getElementById("rows");

days.forEach((day, i) => {
  rows.innerHTML += `
    <tr>
      <td>${day}</td>
      <td><input type="number" id="s${i}" oninput="calc()"></td>
      <td><input type="number" id="p${i}" oninput="calc()"></td>
      <td class="glow" id="r${i}">0</td>
    </tr>
  `;
});

function calc() {
  let ts = 0, tp = 0, tr = 0;

  for (let i = 0; i < 7; i++) {
    let s = +document.getElementById("s"+i).value || 0;
    let p = +document.getElementById("p"+i).value || 0;

    let r = p - s;

    document.getElementById("r"+i).innerText = r.toFixed(2);

    ts += s;
    tp += p;
    tr += r;
  }

  document.getElementById("totalStake").innerText = ts.toFixed(2);
  document.getElementById("totalProfit").innerText = tp.toFixed(2);
  document.getElementById("totalResult").innerText = tr.toFixed(2);
}

function save() {
  let data = [];

  for (let i = 0; i < 7; i++) {
    data.push({
      s: document.getElementById("s"+i).value,
      p: document.getElementById("p"+i).value
    });
  }

  localStorage.setItem("weekBlackGlow", JSON.stringify(data));
  alert("Opgeslagen!");
}

function load() {
  let data = JSON.parse(localStorage.getItem("weekBlackGlow"));
  if (!data) return;

  data.forEach((d, i) => {
    document.getElementById("s"+i).value = d.s;
    document.getElementById("p"+i).value = d.p;
  });

  calc();
}

function reset() {
  localStorage.removeItem("weekBlackGlow");
  location.reload();
}

load();
calc();
</script>

</body>
</html>
