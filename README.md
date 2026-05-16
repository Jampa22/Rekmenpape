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
<title>Geld Management</title>

<style>
body{
margin:0;
height:100vh;
display:flex;
justify-content:center;
align-items:center;
background:#050b18;
font-family:Arial;
font-size:11px;
color:#00d9ff;
}

.box{
width:95%;
max-width:520px;
background:#0b1424;
border:1px solid rgba(0,217,255,0.25);
box-shadow:0 0 18px rgba(0,217,255,0.15);
padding:10px;
}

h2{
text-align:center;
margin:6px 0 10px;
font-size:14px;
text-shadow:0 0 6px #00d9ff;
}

table{
width:100%;
border-collapse:collapse;
}

th,td{
border:1px solid rgba(0,217,255,0.2);
padding:4px;
text-align:center;
}

input{
width:60px;
background:transparent;
border:1px solid #00d9ff;
color:#00d9ff;
text-align:center;
font-size:11px;
outline:none;
}

.total{
color:#7efcff;
font-weight:bold;
}

.week{
margin-top:8px;
text-align:center;
font-size:13px;
color:#ffffff;
text-shadow:0 0 5px rgba(0,217,255,0.4);
}
</style>
</head>

<body>

<div class="box">
<h2>GELD MANAGEMENT</h2>

<table>
<tr>
<th>Dag</th>
<th>Inzet</th>
<th>Winst</th>
<th>Totaal</th>
</tr>

<script>
const dagen=["Ma","Di","Wo","Do","Vr","Za","Zo"];

document.write(
dagen.map(d=>
`<tr>
<td>${d}</td>
<td><input oninput="calc()"></td>
<td><input oninput="calc()"></td>
<td class="total">0</td>
</tr>`
).join("")
);
</script>

</table>

<div class="week">Week totaal: <span id="wk">0</span></div>
</div>

<script>
function calc(){
let rows=document.querySelectorAll("tr");
let week=0;

rows.forEach(r=>{
let inp=r.querySelectorAll("input");
if(inp.length){
let inzet=+inp[0].value||0;
let winst=+inp[1].value||0;
let totaal=winst-inzet;

r.querySelector(".total").innerText=totaal.toFixed(2);
week+=totaal;
}
});

document.getElementById("wk").innerText=week.toFixed(2);
}
</script>

</body>
</html>
