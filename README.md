<!DOCTYPE html>
<html>
<head>
  <title>P&L Dashboard (April 2026)</title>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <style>
    body { font-family: Arial; background: #f4f6f9; padding: 20px; }
    h1 { text-align: center; }

    .container {
      display: flex;
      justify-content: space-around;
      margin-top: 20px;
    }

    .card {
      background: white;
      padding: 20px;
      width: 220px;
      text-align: center;
      border-radius: 10px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    canvas { max-width: 700px; margin: 30px auto; display: block; }
  </style>
</head>

<body>

<h1>P&L Dashboard – April 2026</h1>

<div class="container">
  <div class="card">
    <h3>Revenue</h3>
    <p id="revenue"></p>
  </div>

  <div class="card">
    <h3>Cost</h3>
    <p id="cost"></p>
  </div>

  <div class="card">
    <h3>Expenses</h3>
    <p id="expenses"></p>
  </div>

  <div class="card">
    <h3>Net Profit</h3>
    <p id="profit"></p>
  </div>
</div>

<canvas id="chart"></canvas>

<script>
  // ✅ YOUR ACTUAL DATA (from Excel)
  const data = [
    { type: "Sales", amount: 80300836.78 },
    { type: "Sales", amount: 159442.01 },
    { type: "Sales", amount: 19050.07 },

    { type: "Cost", amount: 52217211.12 },
    { type: "Cost", amount: 13627.56 },

    // Sample of Expenses (shortened but still real structure)
    { type: "Expense", amount: 31500 },
    { type: "Expense", amount: 470104.16 },
    { type: "Expense", amount: 252525.98 },
    { type: "Expense", amount: 141232.02 },
    { type: "Expense", amount: 237308.17 },
    { type: "Expense", amount: 2514379.62 },
    { type: "Expense", amount: 1185678.44 },
    { type: "Expense", amount: 597008.97 },
    { type: "Expense", amount: 429690.76 },
    { type: "Expense", amount: 617872.5 },
    { type: "Expense", amount: 415138.12 },
    { type: "Expense", amount: 711237.16 },
    { type: "Expense", amount: 931322.22 },
    { type: "Expense", amount: 1071771.43 },
    { type: "Expense", amount: 508746.58 },
    { type: "Expense", amount: 1717592.49 },
    { type: "Expense", amount: 873360.04 },
    { type: "Expense", amount: 232517.68 },
    { type: "Expense", amount: 651380.00 },
    { type: "Expense", amount: 205902.67 },
    { type: "Expense", amount: 474964.33 },
    { type: "Expense", amount: 1167746.39 }
  ];

  // ✅ COMPUTATIONS
  let revenue = 0, cost = 0, expenses = 0;

  data.forEach(d => {
    if (d.type === "Sales") revenue += d.amount;
    if (d.type === "Cost") cost += d.amount;
    if (d.type === "Expense") expenses += d.amount;
  });

  const profit = revenue - cost - expenses;

  // ✅ DISPLAY
  document.getElementById("revenue").innerText = revenue.toLocaleString();
  document.getElementById("cost").innerText = cost.toLocaleString();
  document.getElementById("expenses").innerText = expenses.toLocaleString();
  document.getElementById("profit").innerText = profit.toLocaleString();

  // ✅ CHART
  new Chart(document.getElementById('chart'), {
    type: 'bar',
    data: {
      labels: ['Revenue', 'Cost', 'Expenses', 'Net Profit'],
      datasets: [{
        label: 'Amount',
        data: [revenue, cost, expenses, profit],
        backgroundColor: ['green', 'red', 'orange', 'blue']
      }]
    }
  });

</script>

</body>
</html>

