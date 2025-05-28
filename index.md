---
layout: default
title: Meeting Cost Calculator
---

<h1>💼 Meeting Cost Calculator</h1>

<div style="max-width: 600px; margin: auto; font-family: sans-serif;">
  <div style="display: flex; gap: 10px; margin-bottom: 1em;">
    <button onclick="showTab('inputs')">Inputs</button>
    <button onclick="showTab('result')">Result</button>
  </div>

  <div id="inputs" class="tab" style="display: block;">
    <label>Number of people: <input type="number" id="people" value="5" onchange="calculateCost()" /></label><br>
    <label>Avg hourly rate ($): <input type="number" id="rate" value="50" onchange="calculateCost()" /></label><br>
    <label>Duration (minutes): <input type="number" id="minutes" value="60" onchange="calculateCost()" /></label>
  </div>

  <div id="result" class="tab" style="display: none;">
    <p>Total Cost: <strong id="cost">$0.00</strong></p>
  </div>
</div>

<script>
function calculateCost() {
  const people = +document.getElementById("people").value;
  const rate = +document.getElementById("rate").value;
  const minutes = +document.getElementById("minutes").value;
  const cost = people * rate * (minutes / 60);
  document.getElementById("cost").textContent = "$" + cost.toFixed(2);
}

function showTab(id) {
  document.querySelectorAll(".tab").forEach(el => el.style.display = "none");
  document.getElementById(id).style.display = "block";
  if (id === "result") calculateCost();
}
</script>
