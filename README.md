<html lang="nl">
<head>
<meta charset="UTF-8">
<title>Glow Informatie</title>
<style>
/* Glow animatie */
@keyframes glow {
  0%   { box-shadow: 0 0 5px red, 0 0 8px white; }
  50%  { box-shadow: 0 0 12px red, 0 0 18px white; }
  100% { box-shadow: 0 0 5px red, 0 0 8px white; }
}

/* Glowing titel */
h1 {
    text-align: center;
    font-size: 50px;
    color: #ffffff;
    text-shadow:
        0 0 5px #00ffff,
        0 0 10px #00ffff,
        0 0 20px #00ffff,
        0 0 40px #00ffff;
}

/* Glowing tekst blok */
.info {
    max-width: 700px;
    margin: auto;
    font-size: 18px;
    line-height: 1.6;
    padding: 20px;
    border: 1px solid #00ffff;
    border-radius: 10px;
    box-shadow:
        0 0 10px #00ffff,
        0 0 20px #00ffff;
}

/* Knop met glow */
button {
    display: block;
    margin: 30px auto;
    padding: 12px 25px;
    font-size: 16px;
    color: white;
    background: black;
    border: 1px solid #ff00ff;
    cursor: pointer;
    box-shadow:
        0 0 10px #ff00ff,
        0 0 20px #ff00ff;
    transition: 0.3s;
}

button:hover {
    box-shadow:
        0 0 20px #ff00ff,
        0 0 40px #ff00ff;
}
</style>

</head>
<body>

<div class="info">
    If the table previously changed calculation type after a certain number of confirmed spins (causing a loss), stop when that same count is reached again.
</div>


</body>
</html>

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

</html>

<!DOCTYPE html>
<html lang="nl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Week Geld Management</title>

<style>
body {
  background:#0b0f1a;
  font-family: Arial, sans-serif;
  color:#fff;
  display:flex;
  justify-content:center;
  padding:20px;
}

.container {
  width: 520px;
}

h2 {
  text-align:center;
  color:#00ffcc;
  text-shadow:0 0 10px #00ffcc;
}

table {
  width:100%;
  border-collapse: collapse;
  background:#111827;
  box-shadow:0 0 20px #00ffcc33;
  border-radius:10px;
  overflow:hidden;
}

th, td {
  padding:6px;
  text-align:center;
  font-size:12px;
}

th {
  background:#0f172a;
  color:#00ffcc;
}

input {
  width:70px;
  padding:4px;
  border:none;
  border-radius:5px;
  text-align:center;
  background:#1f2937;
  color:#fff;
  outline:none;
}

.glow {
  color:#00ffcc;
  text-shadow:0 0 8px #00ffcc;
  transition:0.3s;
}

.row-anim {
  transition: all 0.3s ease;
}

.total-box {
  margin-top:10px;
  padding:10px;
  background:#111827;
  border-radius:10px;
  text-align:center;
  box-shadow:0 0 15px #00ffcc33;
}

</style>
</head>

<body>

<div class="container">
  <h2>💰 Geld Management Week</h2>

  <table>
    <thead>
      <tr>
        <th>Dag</th>
        <th>Inzet</th>
        <th>Winst</th>
        <th>Totaal</th>
      </tr>
    </thead>
    <tbody id="body"></tbody>
  </table>

  <div class="total-box">
    Week Totaal: <span id="weekTotal" class="glow">0</span>
  </div>
</div>

<script>
const days = ["Maandag","Dinsdag","Woensdag","Donderdag","Vrijdag","Zaterdag","Zondag"];

const body = document.getElementById("body");
const weekTotalEl = document.getElementById("weekTotal");

function createRow(day, i){
  const row = document.createElement("tr");
  row.className = "row-anim";

  row.innerHTML = `
    <td>${day}</td>
    <td><input type="number" id="inzet-${i}" value="0"></td>
    <td><input type="number" id="winst-${i}" value="0"></td>
    <td class="glow" id="total-${i}">0</td>
  `;

  return row;
}

days.forEach((d,i)=>{
  body.appendChild(createRow(d,i));
});

function calc(){
  let weekTotal = 0;

  days.forEach((_,i)=>{
    const inzet = parseFloat(document.getElementById("inzet-"+i).value) || 0;
    const winst = parseFloat(document.getElementById("winst-"+i).value) || 0;

    const total = winst - inzet;

    const totalEl = document.getElementById("total-"+i);
    totalEl.innerText = total.toFixed(2);

    totalEl.style.transform = "scale(1.2)";
    setTimeout(()=> totalEl.style.transform = "scale(1)", 150);

    weekTotal += total;
  });

  weekTotalEl.innerText = weekTotal.toFixed(2);
}

document.addEventListener("input", calc);

calc();
</script>

</body>
</html>
