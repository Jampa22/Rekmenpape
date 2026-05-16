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
<title>Week Winst</title>

<style>
body {
    background: #070b14;
    color: #00f7ff;
    font-family: Arial, sans-serif;
}

h2 {
    text-align: center;
    text-shadow: 0 0 10px #00f7ff;
    margin-bottom: 10px;
}

table {
    margin: auto;
    border-collapse: collapse;
    box-shadow: 0 0 20px #00f7ff33;
    width: 420px;
}

th, td {
    border: 1px solid #00f7ff44;
    padding: 5px;
    text-align: center;
    font-size: 12px;
}

th {
    background: #0e1628;
    text-shadow: 0 0 6px #00f7ff;
}

input {
    width: 70px;
    background: #070b14;
    border: 1px solid #00f7ff55;
    color: #00f7ff;
    text-align: center;
    font-size: 12px;
    outline: none;
}

.result {
    font-weight: bold;
    text-shadow: 0 0 6px #00f7ff;
}

.total {
    font-weight: bold;
    background: #0e1628;
    text-shadow: 0 0 8px #00f7ff;
}
</style>
</head>

<body>

<h2>Week Resultaat</h2>

<table>
<tr>
    <th>Dag</th>
    <th>Inzet</th>
    <th>Winst</th>
    <th>Resultaat</th>
</tr>

<script>
const days = ["Ma","Di","Wo","Do","Vr","Za","Zo"];

document.write(days.map((d,i)=>`
<tr>
<td>${d}</td>
<td><input type="number" oninput="calc()"></td>
<td><input type="number" oninput="calc()"></td>
<td class="result">0</td>
</tr>
`).join(""));

document.write(`
<tr class="total">
<td>Totaal</td>
<td id="totInzet">0</td>
<td id="totWinst">0</td>
<td id="totRes">0</td>
</tr>
`);

function calc(){
    let rows = document.querySelectorAll("tr");
    let totalInzet = 0;
    let totalWinst = 0;

    for(let i=1;i<=7;i++){
        let inzet = rows[i].children[1].children[0].value;
        let winst = rows[i].children[2].children[0].value;

        inzet = parseFloat(inzet) || 0;
        winst = parseFloat(winst) || 0;

        let res = winst - inzet;
        rows[i].children[3].innerText = res.toFixed(2);

        totalInzet += inzet;
        totalWinst += winst;
    }

    document.getElementById("totInzet").innerText = totalInzet.toFixed(2);
    document.getElementById("totWinst").innerText = totalWinst.toFixed(2);
    document.getElementById("totRes").innerText = (totalWinst - totalInzet).toFixed(2);
}
</script>

</table>

</body>
</html>
