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

<html lang="nl">
<head>
<meta charset="UTF-8">
<title>MM Week</title>

<style>
body{
  background:#0f0f0f;
  color:#fff;
  font-family:Arial;
  padding:10px;
}

h2{
  text-align:center;
  color:#00ffcc;
  text-shadow:0 0 6px #00ffcc;
  font-size:15px;
  margin-bottom:10px;
}

table{
  width:100%;
  max-width:520px;
  margin:auto;
  border-collapse:collapse;
}

th,td{
  border:1px solid #222;
  padding:4px;
  text-align:center;
  font-size:12px;
}

th{color:#00ffcc;}

input{
  width:55px;
  background:#111;
  border:1px solid #333;
  color:#00ffcc;
  text-align:center;
  font-size:12px;
}

.glow{
  color:#00ffcc;
  text-shadow:0 0 5px #00ffcc;
}

footer{
  text-align:center;
  margin-top:10px;
  font-size:14px;
}
</style>
</head>

<body>

<h2>Money Management Week</h2>

<table>
<thead>
<tr>
<th>Dag</th>
<th>Inzet</th>
<th>Winst</th>
<th>Totaal</th>
</tr>
</thead>

<tbody id="rows"></tbody>
</table>

<footer>
Week totaal: <span id="week" class="glow">0</span>
</footer>

<script>
const days=["Ma","Di","Wo","Do","Vr","Za","Zo"];

const rows=document.getElementById("rows");

days.forEach((d,i)=>{
  rows.innerHTML+=`
  <tr>
    <td>${d}</td>
    <td><input id="i${i}" oninput="calc()"></td>
    <td><input id="w${i}" oninput="calc()"></td>
    <td class="glow" id="t${i}">0</td>
  </tr>`;
});

function calc(){
  let week=0;

  for(let i=0;i<7;i++){
    let iVal=+document.getElementById("i"+i).value||0;
    let wVal=+document.getElementById("w"+i).value||0;

    let total=wVal-iVal;
    document.getElementById("t"+i).innerText=total.toFixed(2);

    week+=total;
  }

  document.getElementById("week").innerText=week.toFixed(2);
}

calc();
</script>

</body>
</html>
