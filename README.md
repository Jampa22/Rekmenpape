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
<meta charset="UTF-8">
<title>Week Tracker</title>
<style>
body{
    background:#0f111a;
    color:#e6e6e6;
    font-family:Arial;
    margin:0;
    padding:20px;
}

h2{ text-align:center; color:#00ffd5; }

table{
    width:100%;
    border-collapse:collapse;
    margin-top:10px;
}

th, td{
    border:1px solid #2a2f3a;
    padding:8px;
    text-align:center;
}

input{
    width:80px;
    padding:5px;
    background:#1a1f2b;
    border:1px solid #333;
    color:#fff;
    border-radius:5px;
}

button{
    padding:10px 15px;
    margin-top:10px;
    border:none;
    border-radius:8px;
    cursor:pointer;
}

#okBtn{
    background:#00ffd5;
    color:#000;
    font-weight:bold;
}

#resetBtn{
    background:#ff4d4d;
    color:#fff;
}

.footer{
    position:fixed;
    bottom:0;
    left:0;
    width:100%;
    background:#111522;
    padding:10px;
    display:flex;
    justify-content:space-around;
    border-top:1px solid #2a2f3a;
    font-size:14px;
}

.small{
    font-size:12px;
    opacity:0.8;
}
</style>
</head>
<body>

<h2>Week Overzicht</h2>

<table id="weekTable">
<tr>
    <th>Dag</th>
    <th>Actief</th>
    <th>Inzet</th>
    <th>Winst</th>
</tr>

<script>
const days = ["Ma","Di","Wo","Do","Vr","Za","Zo"];
document.write(
days.map((d,i)=>`
<tr>
<td>${d}</td>
<td><input type="checkbox" id="c${i}" checked></td>
<td><input type="number" id="i${i}" value="0"></td>
<td><input type="number" id="w${i}" value="0"></td>
</tr>
`).join("")
);
</script>

</table>

<div style="text-align:center;">
    <button id="okBtn" onclick="bereken()">OK Berekenen</button>
    <button id="resetBtn" onclick="resetAll()">Reset</button>
</div>

<div class="footer">
    <div class="small">Totaal Inzet: <span id="tInzet">0</span></div>
    <div class="small">Totaal Winst: <span id="tWinst">0</span></div>
    <div class="small">Netto Week: <span id="tNetto">0</span></div>
</div>

<script>
function bereken(){
    let inzet = 0;
    let winst = 0;

    for(let i=0;i<7;i++){
        if(document.getElementById("c"+i).checked){
            inzet += Number(document.getElementById("i"+i).value || 0);
            winst += Number(document.getElementById("w"+i).value || 0);
        }
    }

    document.getElementById("tInzet").innerText = inzet;
    document.getElementById("tWinst").innerText = winst;
    document.getElementById("tNetto").innerText = (winst - inzet);
}

// auto berekenen bij invoer
document.addEventListener("input", bereken);

function resetAll(){
    for(let i=0;i<7;i++){
        document.getElementById("c"+i).checked = true;
        document.getElementById("i"+i).value = 0;
        document.getElementById("w"+i).value = 0;
    }
    bereken();
}

bereken();
</script>

</body>
</html>
