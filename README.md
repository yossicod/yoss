# yoss
t,r dd
<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>גרף מניות</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f5f5f5;
    }

    header {
      background: #ffffff;
      padding: 10px;
      display: flex;
      gap: 10px;
      align-items: center;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }

    input {
      padding: 8px;
      font-size: 16px;
      width: 200px;
    }

    button {
      padding: 8px 12px;
      font-size: 16px;
      cursor: pointer;
    }

    #chart {
      height: calc(100vh - 60px);
    }
  </style>
</head>
<body>

<header>
  <strong>סימול מניה:</strong>
  <input id="symbolInput" placeholder="NASDAQ:AAPL">
  <button onclick="loadChart()">הצג גרף</button>
</header>

<div id="chart"></div>

<script src="https://s3.tradingview.com/tv.js"></script>
<script>
  let widget;

  function loadChart() {
    const symbol = document.getElementById("symbolInput").value || "NASDAQ:AAPL";

    if (widget) {
      document.getElementById("chart").innerHTML = "";
    }

    widget = new TradingView.widget({
      container_id: "chart",
      symbol: symbol,
      interval: "D",
      autosize: true,
      locale: "he",
      theme: "light",
      hide_side_toolbar: false,
      allow_symbol_change: true,
      withdateranges: true,
      studies: []
    });
  }

  loadChart();
</script>

</body>
</html>
