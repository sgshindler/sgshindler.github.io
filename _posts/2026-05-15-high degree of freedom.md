---
title: 'Higher Degree of Freedom Systems'
date: 2026-05-15
permalink: /posts/2026/05/Higher Degree of Freedom Systems/
tags:
  - heuristics
---
In the last post, I talked about the two factors which are required to give exponential behavor in a system. First, the system has to have only one degree of freedom, and second, the rate of change in the system needs to be linearly related to its state. The ubiquity of the linear limit explains why this second factor would be common, but the requirement that the system state be defined by one variable (one degree of freedom) is more abstract. Let's dig a little deeper into this idea of degrees of freedom.

First of all, in the type of analysis I'm presenting here, we're using differential equations to model the systems under question. The study of differential equations is quite involved, and not something I can cover fully here. If my discussion feels limited, or if you find yourself having questions beyond this here is one option: 

https://www.math.unl.edu/~jlogan1/PDFfiles/New3rdEditionODE.pdf 

Now, back to the problem at hand. One of the most important properties of a differential equation is it's "order". The order of a differential equation is simply the highest derivative. The differential equation which gives exponential behavior

$${dy}/{dt} = ay+b$$

is first order, becuase the highest derivative is a first derivative. An expression like:

$${d^2y}/{dt^2} = ay+b$$

would be second order, becuase the highest derivative is a second derivative. In my discussion I'm going to use a useful property of differential equations to avoid any discussion of these higher order differential equations. Any higher order differential equation can be written as a system of first order differential equations. So the second order differential equation I just wrote out would now be,

$${dy_1}/{dt} = ay_2+b$$

$${dy_2}/{dt} = y_1

Now, we can see that these higher order differential equations correspond to higher degree of freedom systems. In this case, our second order system is a 2 degree of freedom system. You need to know the value of $$y_1$$ and $$y_2$$ in order to know the future state of the system. To explore this, let's look at the linear second order system, which becomes,

$${dy_1}/{dt} = a+by_1+cy_2$$

$${dy_2}/{dt} = d+ey_1+fy_2$$

let

$$z = a+by_1+cy_2$$

$${dy_1}/{dt} = z$$

$${dz}/{dt} = b{dy_1}/{dt}+c{dy_2}/{dt} = cd-fa+(ce-fb)y_1+(f+b)z$$

which gives:

$${d^2y_1}/{dt^2} = cd-fa+(ce-fb)y_1+(f+b){dy_1}/{dt}$$

Solving this equation gives us a decaying oscillation. 

<style>
.controls {
  margin-bottom: 1rem;
}

.control {
  margin: 0.5rem 0;
}

label {
  display: inline-block;
  width: 20px;
}

.value {
  display: inline-block;
  width: 60px;
  font-family: monospace;
}
</style>

<div class="controls">

  <div class="control">
    <label>a</label>
    <input type="range" id="a" min="-5" max="5" step="0.1" value="0">
    <span class="value" id="aVal">0</span>
  </div>

  <div class="control">
    <label>b</label>
    <input type="range" id="b" min="-5" max="5" step="0.1" value="-1">
    <span class="value" id="bVal">-1</span>
  </div>

  <div class="control">
    <label>c</label>
    <input type="range" id="c" min="-5" max="5" step="0.1" value="0">
    <span class="value" id="cVal">0</span>
  </div>

</div>

<div id="plot" style="width:100%;height:500px;"></div>

<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>

<script>
function solveODE(a, b, c) {

  // Convert second-order ODE into two first-order equations:
  // y1 = y
  // y2 = dy/dt
  //
  // dy1/dt = y2
  // dy2/dt = a + b*y1 + c*y2

  const dt = 0.02;
  const tMax = 20;

  const t = [];
  const y = [];

  let y1 = 1.0;   // initial position
  let y2 = 0.0;   // initial velocity

  for (let time = 0; time <= tMax; time += dt) {

    t.push(time);
    y.push(y1);

    // Euler integration
    const dy1 = y2;
    const dy2 = a + b * y1 + c * y2;

    y1 += dt * dy1;
    y2 += dt * dy2;
  }

  return { t, y };
}

function updatePlot() {

  const a = parseFloat(document.getElementById('a').value);
  const b = parseFloat(document.getElementById('b').value);
  const c = parseFloat(document.getElementById('c').value);

  document.getElementById('aVal').textContent = a;
  document.getElementById('bVal').textContent = b;
  document.getElementById('cVal').textContent = c;

  const sol = solveODE(a, b, c);

  const trace = {
    x: sol.t,
    y: sol.y,
    mode: 'lines',
    type: 'scatter',
    name: 'y(t)'
  };

  const layout = {
    title: 'Solution of y\\" = a + by + cy\\"',
    xaxis: {
      title: 't'
    },
    yaxis: {
      title: 'y(t)'
    },
    margin: {
      t: 50
    }
  };

  Plotly.newPlot('plot', [trace], layout, {
    responsive: true
  });
}

['a', 'b', 'c'].forEach(id => {
  document.getElementById(id).addEventListener('input', updatePlot);
});

updatePlot();
</script>
```

It turns out that no matter how non-linear you make your 1-DOF model, you can never obtain oscillations. Notably however, there are states in which this second order equation can give exponential behavior - part of why the exponential behavior is so common. So if a phenomenon is ever oscillatory, it's oscillatory because there are more than one degree of freedom in the underlying system. Similar insights can be made about higher-order systems. By understanding the degrees of freedom which underpin a system allows you to understand how it will behave. The number of degrees of freedom is the fundamental number which defines the qualitative behavior of the system.

So, I've talked about systems which vary over time (or any other single dimension), but many important physical problems don't just vary over one dimension, instead, they vary over many. One possible instance of this would be the variation of a field over space and time. The key issue here is that often these fields are not just a single number, but are instead a vector or tensor object. If we want to apply the same type of analysis to problems which vary over space and time, it is key to understand the properties of these other mathematical objects.
