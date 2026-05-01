<div id="output">Choose the following number</div>

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
