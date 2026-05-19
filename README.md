<p style="color: green;">The Most Powerfull Prediction Tool</p>

<html lang="nl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Week Schema</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    background:#050505;
    font-family:Arial,sans-serif;
    padding:8px;
    color:white;
}

/* WRAPPER */
.container{
    width:100%;
    max-width:420px;
    margin:auto;
    background:#0e0e0e;
    border-radius:16px;
    padding:12px;

    box-shadow:
        0 0 15px #00ffae55,
        0 0 30px #00ffae22;
}

/* TITLE */
.title{
    text-align:center;
    font-size:20px;
    margin-bottom:10px;
    color:white;

    text-shadow:
        0 0 5px #fff,
        0 0 10px #00ffae,
        0 0 20px #00ffae;
}

/* GRID */
.header,
.row{
    display:grid;
    grid-template-columns: 45px 1fr 1fr 1fr;
    gap:5px;
    align-items:center;
}

.header{
    font-size:11px;
    font-weight:bold;
    text-align:center;
    margin-bottom:6px;
    color:white;
    text-shadow:0 0 8px #00ffae;
}

.row{
    margin-bottom:6px;
}

/* INPUT BOXES */
.box{
    width:100%;
    border:none;
    border-radius:8px;
    padding:8px 4px;
    text-align:center;
    font-size:11px;
    color:white;
    background:#1b1b1b;
    outline:none;

    box-shadow:
        0 0 6px #00ffae33,
        0 0 12px #00ffae11;

    text-shadow:0 0 5px #00ffae;
}

.day{
    font-weight:bold;
}

/* NETTO CEL */
.result{
    background:#0c0c0c;
    font-weight:bold;
}

/* NETTO BOX */
.nettoBox{
    margin-top:10px;
    background:#0c0c0c;
    border-radius:12px;
    padding:10px;
    text-align:center;

    box-shadow:
        0 0 10px #00ffae55,
        0 0 20px #00ffae22;
}

.nettoTitle{
    font-size:12px;
    margin-bottom:4px;
    text-shadow:0 0 6px #00ffae;
}

.nettoValue{
    font-size:22px;
    font-weight:bold;
    text-shadow:
        0 0 5px #fff,
        0 0 15px #00ffae;
}

/* BUTTONS */
.buttons{
    display:flex;
    gap:6px;
    margin-top:10px;
}

button{
    flex:1;
    border:none;
    border-radius:10px;
    padding:10px;
    font-size:12px;
    font-weight:bold;
    cursor:pointer;
    transition:0.2s;
}

/* OPSLAAN (WIT + GROEN GLOW) */
.saveBtn{
    background:#00ffae;
    color:white;

    box-shadow:
        0 0 10px #00ffae88,
        0 0 20px #00ffae33;

    text-shadow:0 0 6px #000;
}

/* RESET (ORANGE + WIT TEKST) */
.resetBtn{
    background:#bfffe9;
    color:white;

    box-shadow:
        0 0 10px #bfffe988,
        0 0 20px #bfffe933;

    text-shadow:0 0 6px #000;
}

/* HOVER */
button:hover{
    transform:scale(1.02);
}

/* PLACEHOLDER */
input::placeholder{
    color:#888;
}

</style>
</head>

<body>

<div class="container">

    <div class="title">Ringkesan Minggu</div>

    <div class="header">
        <div>Dag</div>
        <div>Inzet</div>
        <div>Totaal</div>
        <div>Netto Winst</div>
    </div>

    <div id="schema"></div>

    <div class="nettoBox">
        <div class="nettoTitle">Totaal Netto Week Winst</div>
        <div class="nettoValue" id="grandTotal">€0.00</div>
    </div>

    <div class="buttons">
        <button class="saveBtn" onclick="saveData()">Opslaan</button>
        <button class="resetBtn" onclick="resetData()">Opnieuw</button>
    </div>

</div>

<script>

const dagen = ["Ma","Di","Wo","Do","Vr","Za","Zo"];

const schema = document.getElementById("schema");

dagen.forEach((dag,index)=>{

    schema.innerHTML += `
    <div class="row">

        <div class="box day">${dag}</div>

        <input type="number"
               class="box"
               id="inzet${index}"
               placeholder="€"
               oninput="bereken(${index})">

        <input type="number"
               class="box"
               id="winst${index}"
               placeholder="€"
               oninput="bereken(${index})">

        <div class="box result"
             id="result${index}">
             €0.00
        </div>

    </div>`;
});

function bereken(index){

    let inzet =
        parseFloat(document.getElementById(`inzet${index}`).value) || 0;

    let winst =
        parseFloat(document.getElementById(`winst${index}`).value) || 0;

    let netto = winst - inzet;

    document.getElementById(`result${index}`).innerText =
        "€" + netto.toFixed(2);

    updateNetto();
}

function updateNetto(){

    let totaal = 0;

    dagen.forEach((_,index)=>{

        let inzet =
            parseFloat(document.getElementById(`inzet${index}`).value) || 0;

        let winst =
            parseFloat(document.getElementById(`winst${index}`).value) || 0;

        totaal += (winst - inzet);

    });

    document.getElementById("grandTotal").innerText =
        "€" + totaal.toFixed(2);
}

function saveData(){

    let data = [];

    dagen.forEach((_,index)=>{

        data.push({
            inzet: document.getElementById(`inzet${index}`).value,
            winst: document.getElementById(`winst${index}`).value
        });

    });

    localStorage.setItem("weekSchema", JSON.stringify(data));

    alert("Opgeslagen");
}

function resetData(){

    localStorage.removeItem("weekSchema");
    location.reload();
}

loadData();

function loadData(){

    let data = JSON.parse(localStorage.getItem("weekSchema"));

    if(!data) return;

    data.forEach((item,index)=>{

        document.getElementById(`inzet${index}`).value = item.inzet;
        document.getElementById(`winst${index}`).value = item.winst;

        bereken(index);
    });

    updateNetto();
}

</script>

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



<div id="output">Choose the following number</div>

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
      output.textContent = "Nummer " + i + " heeft nog geen uitkomst ingesteld.";
    } else {
      output.textContent = "🎯 Nummer " + i + " → " + data[i];
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

