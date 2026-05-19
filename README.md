<!-- FIXED MINI GUIDE -->
<style>
#miniGuide{
    position:fixed; /* blijft vast staan */
    top:6px;
    left:6px;
    z-index:999999;
    font-family:Arial,sans-serif;
}

/* Kleine knop */
#guideToggle{
    width:28px;
    height:28px;
    border:none;
    border-radius:8px;
    background:#050505;
    color:#baffea;
    cursor:pointer;
    font-size:14px;

    display:flex;
    align-items:center;
    justify-content:center;

    box-shadow:
        0 0 8px #9fffe3,
        0 0 18px rgba(159,255,227,.35),
        inset 0 0 5px rgba(255,255,255,.05);
}

/* Popup */
#guideContent{
    position:absolute;
    top:36px;
    left:0;

    width:220px;
    padding:10px;

    border-radius:12px;
    background:rgba(8,8,8,.97);
    border:1px solid rgba(186,255,234,.15);

    display:none;

    color:white;

    box-shadow:
        0 0 20px rgba(159,255,227,.15);
}

.guideItem{
    padding:7px 0;
    border-bottom:1px solid rgba(255,255,255,.06);
}

.guideItem:last-child{
    border-bottom:none;
}

.guideTitle{
    color:#baffea;
    font-size:11px;
    font-weight:bold;
    margin-bottom:3px;
}

.guideText{
    color:#d8d8d8;
    font-size:10px;
    line-height:1.4;
}
</style>

<div id="miniGuide">

    <!-- BUTTON -->
    <button id="guideToggle">☰</button>

    <!-- CONTENT -->
    <div id="guideContent">

        <div class="guideItem">
            <div class="guideTitle">🎯Predictions</div>
            <div class="guideText">
                Live trend prediction system.
            </div>
        </div>

        <div class="guideItem">
            <div class="guideTitle">📈Patterns</div>
            <div class="guideText">
                Detects repeating streaks and switches.
            </div>
        </div>

        <div class="guideItem">
            <div class="guideTitle">📊Data</div>
            <div class="guideText">
                Uses live table confirmations and statistics.
            </div>
        </div>

        <div class="guideItem">
            <div class="guideTitle">📉Exit signals</div>
            <div class="guideText">
                Stop when repeated loss behavior returns.
            </div>
        </div>

        <div class="guideItem">
            <div class="guideTitle">⭐️Optimize</div>
            <div class="guideText">
                Dynamic optimization for stable calculations.
            </div>
        </div>

        <div class="guideItem">
            <div class="guideTitle">🔥Hot tables</div>
            <div class="guideText">
                Highlights strong and stable tables.
            </div>
        </div>

    </div>

</div>

<script>
const toggleBtn = document.getElementById("guideToggle");
const guideContent = document.getElementById("guideContent");

toggleBtn.onclick = () => {
    guideContent.style.display =
        guideContent.style.display === "block"
        ? "none"
        : "block";
};
</script>

<p style="color: green;">The Most Powerfull Prediction Tool</p>

<!DOCTYPE html>
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
    padding:6px;
    color:white;
}

/* CONTAINER */
.container{
    width:100%;
    max-width:420px;
    margin:auto;
    background:#0e0e0e;
    border-radius:14px;
    padding:10px;

    box-shadow:
        0 0 14px #00ffae55,
        0 0 26px #00ffae22;
}

/* TITLE */
.title{
    text-align:center;
    font-size:18px;
    margin-bottom:8px;

    color:white;
    text-shadow:
        0 0 4px #fff,
        0 0 10px #00ffae,
        0 0 18px #00ffae;
}

/* GRID */
.header,
.row{
    display:grid;
    grid-template-columns: 40px 1fr 1fr 1fr;
    gap:4px;
    align-items:center;
}

.header{
    font-size:10px;
    font-weight:bold;
    text-align:center;
    margin-bottom:5px;
    color:white;
    text-shadow:0 0 6px #00ffae;
}

.row{
    margin-bottom:4px;
}

/* INPUT BOX */
.box{
    width:100%;
    border:none;
    border-radius:7px;
    padding:7px 3px;

    font-size:10px;
    text-align:center;

    background:#151515;
    color:white;

    outline:none;

    transition:0.2s;

    box-shadow:
        0 0 5px #00ffae22,
        0 0 10px #00ffae11;

    text-shadow:0 0 4px #00ffae;
}

/* GLOW ON FOCUS / CLICK */
.box:focus{
    box-shadow:
        0 0 8px #00ffae,
        0 0 18px #00ffae88;
    transform:scale(1.03);
}

/* DAY */
.day{
    font-weight:bold;
}

/* RESULT */
.result{
    background:#0c0c0c;
    font-weight:bold;
}

/* NETTO */
.nettoBox{
    margin-top:8px;
    padding:8px;

    border-radius:10px;
    background:#0c0c0c;

    text-align:center;

    box-shadow:
        0 0 10px #00ffae44,
        0 0 18px #00ffae22;
}

.nettoTitle{
    font-size:11px;
    margin-bottom:3px;
    text-shadow:0 0 6px #00ffae;
}

.nettoValue{
    font-size:18px;
    font-weight:bold;

    text-shadow:
        0 0 4px #fff,
        0 0 12px #00ffae;
}

/* BUTTONS */
.buttons{
    display:flex;
    gap:5px;
    margin-top:8px;
}

button{
    flex:1;
    border:none;
    border-radius:8px;
    padding:9px;
    font-size:11px;
    font-weight:bold;
    cursor:pointer;
    transition:0.2s;
}

/* SAVE */
.saveBtn{
    background:#00ffae;
    color:white;

    box-shadow:
        0 0 10px #00ffae88,
        0 0 20px #00ffae33;

    text-shadow:0 0 6px #000;
}

/* RESET */
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

input::placeholder{
    color:#777;
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
        <div class="nettoTitle">Totaal Netto Winst</div>
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
               onfocus="this.classList.add('active')"
               onblur="this.classList.remove('active')"
               oninput="bereken(${index})">

        <input type="number"
               class="box"
               id="winst${index}"
               placeholder="€"
               onfocus="this.classList.add('active')"
               onblur="this.classList.remove('active')"
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

</body>
</html>

<html lang="nl">
<head>
<meta charset="UTF-8">
<title>Glow Informatie</title>

<style>
body {
    background-color: #0a0a0a;
    color: white;
    font-family: Arial, sans-serif;
    padding: 40px;
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


