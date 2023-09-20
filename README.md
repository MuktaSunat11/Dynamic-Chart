# Dynamic-Chart with Real-Time-Data
This is a simple real-time chart that demonstrates how to use Chart.js to create a line chart that updates in real time.
## Html file
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Real-Time Chart</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div id="div">
      <canvas id="realTimeChart"></canvas>
    </div>

    <script src="script.js"></script>
  </body>
</html>
```
## Css file
```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  canvas {
    max-width: 100%;
    height: auto;
  }
  #div {
    width: 80%;
    margin: auto;
  }
```
## Javascript file
```
const ctx = document.getElementById("realTimeChart").getContext("2d");
let chart;
const initialData = {
  labels: [],
  datasets: [
    {
      label: "Price",
      data: [],
      borderColor: "rgba(75, 192, 192, 1)",
      borderWidth: 1,
      fill: false,
    },
  ],
};
const chartConfig = {
  type: "line",
  data: initialData,
  options: {
    scales: {
      x: {
        type: "linear",
        position: "bottom",
        title: {
          display: true,
          text: "Time",
        },
      },
      y: {
        beginAtZero: true,
        title: {
          display: true,
          text: "Price",
        },
      },
    },
    animation: false,
  },
};
chart = new Chart(ctx, chartConfig);
function addData() {
  const newData = Math.random() * 500;
  chart.data.labels.push(chart.data.labels.length);
  chart.data.datasets[0].data.push(newData);
  chart.update();
}
setInterval(addData, 1000);
```
