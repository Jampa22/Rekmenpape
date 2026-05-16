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
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Money Week</title>

<style>
body{
  background:#05070f;
  font-family: Arial;
  display:flex;
  justify-content:center;
  padding:10px;
  color:white;
}

.box{
  width:360px;
}

h3{
  text-align:center;
  color:#00ffd5;
  text-shadow:0 0 10px #00ffd5;
  margin:8px 0;
  font-size:16px;
}

table{
  width:100%;
  border-collapse:collapse;
  background:#0d1424;
  border-radius:10px;
  overflow:hidden;
  box-shadow:0 0 20px #00ffd533;
}

th,td{
  font-size:11px;
  padding:4px;
  text-align:center;
}

th{
  background:#111b33;
  color:#00ffd5;
}

input{
  width:55px;
  font-size:11px;
  padding:3px;
  border:none;
  border-radius:5px;
  text-align:center;
  background:#1b2742;
  color:white;
  outline:none;
}

.glow{
  color:#00ffd5;
  text-shadow:0 0 8px #00ffd5;
  transition:0.2s;
}

.pop{
  transform:scale(1.2);
}

.footer{
  margin-top:8px;
  background:#0d1424;
  padding:8px;
  border-radius:10px;
  text-align:center;
  font-size:12px;
  box-shadow:0 0 15px #00ffd533;
}
</style>
</head>

<body>

<div class="box">
  <h3>💰 Money Manager</h3>

  <table>
    <thead>
      <tr>
        <th>Dag</th>
        <th>Inzet</th>
        <th>Winst</th>
        <th>Totaal</th>
      </tr>
    </thead>
    <tbody id="t"></tbody>
  </table>

  <div class="footer">
    Week Totaal: <span id="week" class="glow">0</span>
  </div>
</div>

<script>
const days=["Ma","Di","Wo","Do","Vr","Za","Zo"];
const t=document.getElementById("t");
const week=document.getElementById("week");

days.forEach((d,i)=>{
  t.innerHTML+=`
    <tr>
      <td>${d}</td>
      <td><input id="i${i}" type="number" value="0"></td>
      <td><input id="w${i}" type="number" value="0"></td>
      <td class="glow" id="r${i}">0</td>
    </tr>
  `;
});

function calc(){
  let sum=0;

  days.forEach((_,i)=>{
    let iVal=+document.getElementById("i"+i).value||0;
    let wVal=+document.getElementById("w"+i).value||0;

    let res=wVal-iVal;
    let el=document.getElementById("r"+i);

    el.innerText=res.toFixed(2);

    el.classList.add("pop");
    setTimeout(()=>el.classList.remove("pop"),150);

    sum+=res;
  });

  week.innerText=sum.toFixed(2);
}

document.addEventListener("input",calc);
calc();
</script>

</body>
</html>
