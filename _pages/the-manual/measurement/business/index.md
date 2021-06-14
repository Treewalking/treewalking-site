---
permalink: /the-manual/measurement/business/
title: "The Manual - Measurement - Business"
layout: single
sidebar:
  nav: "manual"
header:
  overlay_color: "#5e616c"
  overlay_image: "/assets/images/manual-feature.jpg"
categories:
  - Manual
tags:
  - manual
---

{% include toc %}

## Introduction

## Business Value

Business 
<div>
  <canvas id="myChart"></canvas>
</div>


## 




<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<script>

  const DATA_COUNT = 26;
  const labels = [];
  const datapoints = [];
  var next = 2;
  var previous = 1;
  for (let i = 0; i < DATA_COUNT; ++i) {
    labels.push(i.toString()); 
    var graph = previous + next;
    datapoints.push(graph);
    previous = next;
    next = graph;
  }

  for (let i = 0; i < DATA_COUNT; ++i) {
    labels.push((i+DATA_COUNT).toString()); 
    datapoints.push(datapoints[i+DATA_COUNT-1] + datapoints[DATA_COUNT-i-1]);
  }

  const data = {
    labels: labels,
    datasets: [
      {
        label: 'Business Value',
        data: datapoints,
        borderColor: 'rgb(255, 99, 132)',
        fill: false,
        cubicInterpolationMode: 'monotone',
        tension: 0.4
      }
    ]
  };   

  const config = {
    type: 'line',
    data: data,
    options: {
      responsive: true,
      plugins: {
        title: {
          display: true,
          text: 'Business Value Released Over Time'
        },
      },
      interaction: {
        intersect: false,
      },
      scales: {
        x: {
          display: true,
          title: {
            display: true,
            text: 'Time'
          }
        },
        y: {
          display: false,
          title: {
            display: true,
            text: 'Value'
          }
        }
      }
    },
  };

  var myChart = new Chart(
      document.getElementById('myChart'),
      config
    );

</script>

