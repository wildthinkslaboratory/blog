---
layout: post
title: Triptych Layouts for Complex Explanations
date: 2020-01-01
smartdown: true
comments: false
background: '/img/posts/triptych.jpg'
---

I'm breaking an explanation down into three parts: the high level ideas, a picture of the model, and symbolic reasoning. My friend [Dan](https://doctorbud.com) gave me the idea of using a [triptych](https://en.wikipedia.org/wiki/Triptych) approach for displaying the three parts of the explanation.  

![halfwidth](https://upload.wikimedia.org/wikipedia/commons/b/bf/Annunciation_Triptych_%28Merode_Altarpiece%29_MET_DP273206.jpg)

Why am I only using two boxes?

#### --outlinebox outer1

#### --outlinebox left1

```javascript /playable/autoplay
//smartdown.import=https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraphcore.js

smartdown.importCssUrl('https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraph.css');
myDiv = this.div;

myDiv.innerHTML = `<div id='box1' class='jxgbox' style='height:500px'>`;


JXG.Options.axis.ticks.majorHeight = 40;
// create the board
board0 = JXG.JSXGraph.initBoard('box1', {boundingbox:[-5,10,5,-3], showCopyright:false, keepaspectratio:false, axis:false});
board0.resizeContainer(myDiv.offsetWidth, myDiv.offsetHeight);

let xaxis = board0.create('axis', [[0, 0], [1,0]], 
      {name:'x', 
      withLabel: true,
      label: {
        fontSize: 20,
        position: 'rt',  // possible values are 'lft', 'rt', 'top', 'bot'
        offset: [-20, 20]   // (in pixels)
      }
      });
let yaxis = board0.create('axis', [[0, 0], [0, 1]], 
      {name:'y', 
      withLabel: true, 
      label: {
        fontSize: 20,
        position: 'rt',  // possible values are 'lft', 'rt', 'top', 'bot'
        offset: [-30, -20]   // (in pixels)
        }
      });   

// parabala and it's derivative
let f = function(x) { return  x*x; };
let df = function(x) { return 2*x; }
let x = board0.create('glider', [2,0, xaxis], {name:'x', size:6});
let fx = board0.create('point', [
  function() { return x.X(); }, 
  function() { return f(x.X()); }], {name:'', color:'#222299', fixed:true});
let graph_f = board0.create('functiongraph', [f,-10,10], {strokeColor:'#999999'});
let graph_df = board0.create('functiongraph', [df,-10,10], {strokeColor:'#44AA44', visible:false});
let dfx = board0.create('point', [
  function() { return x.X(); }, 
  function() { return df(x.X()); }], {name:'', color:'#44AA44', fixed:true, visible:false});

// tangent line section
let tangent = board0.create('line', [
  function() { return f(x.X());},
  function() { return - df(x.X());},
  1], {color:'#222299', visible:true});
let tangentSlopeText = board0.create('text',[
  function() { return x.X() + 0.5; },
  function() { return f(x.X()) + 0.5;},
  function(){ return 'slope = '+ df(x.X()).toFixed(2); }], {fontSize:15, visible:true});


// Secant line section
// the slider point for the secant
let x_h = board0.create('glider', [x.X() + 3, 0, xaxis], {name:'x + h', size:6, color:'green', visible:false} ); 

let highlightFon = function() {
  graph_f.setAttribute({strokeColor:'#33FFFF', strokeWidth:3});
};

let highlightFoff = function() {
  graph_f.setAttribute({strokeColor:'#999999', strokeWidth:1});
};

window.highlightFoff = highlightFoff;
window.highlightFon = highlightFon;

this.sizeChanged = function() {      
  board0.resizeContainer(myDiv.offsetWidth, myDiv.offsetHeight);
};

 
```
#### --outlinebox


#### --outlinebox right1

### Finding the Derivative
The derivative of a function $f(x)=x^2$ tells us the **slope** of the tangent line. Drag the red dot to see the slope of the tangent line for different values of $x$.

How do we figure out what the slope is for each value of $x$?

#### --outlinebox
#### --outlinebox


```javascript /autoplay

smartdown.importCssCode(
`
.outer {
 
}

.left {
  padding-top: 40px; 
}

.right {
  padding-left: 20px;
  padding-right: 20px;
  font-size: 18px;
}

.highlightOn {
  background-color: #33FFFF;
}

.highlightOff {
  background-color: #CCCCCC;
}

@media (min-width: 800px) {
  .outer {
   
  }

  .left {
    width: 50%;
    display: inline-block;
    vertical-align: top;
  }

  .right {
    width: 48%;
    display: inline-block;
    vertical-align: top;
  }
}
`);


const outer = document.getElementById('outer1');
const left = document.getElementById('left1');
const right = document.getElementById('right1');

outer.classList.remove('decoration-outlinebox');
left.classList.remove('decoration-outlinebox');
right.classList.remove('decoration-outlinebox');

outer.classList.add('outer');
left.classList.add('left');
right.classList.add('right');

const math1 = document.getElementById('MathJax-Element-1-Frame');
math1.onmouseover = logMouseOver;
math1.onmouseout = logMouseOut;
math1.classList.add('highlightOff');

function logMouseOver() {
  math1.classList.add('highlightOn');
  math1.classList.remove('highlightOff');
  highlightFon();
}

function logMouseOut() {
  math1.classList.add('highlightOff');
  math1.classList.remove('highlightOn');
  highlightFoff();
}

```


### Derivatives are Slopes
#### --outlinebox outer2

#### --outlinebox left2

```javascript /playable/autoplay
//smartdown.import=https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraphcore.js

smartdown.importCssUrl('https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraph.css');

const myDiv = this.div;
myDiv.innerHTML = `<div id='box2' class='jxgbox' style='height:500px'>`;

JXG.Options.axis.ticks.majorHeight = 40;
// create the board
board1 = JXG.JSXGraph.initBoard('box2', {boundingbox:[-5,10,5,-3], showCopyright:false, keepaspectratio:false, axis:false});
board1.resizeContainer(myDiv.offsetWidth, myDiv.offsetHeight);

let xaxis = board1.create('axis', [[0, 0], [1,0]], 
      {name:'x', 
      withLabel: true,
      label: {
        fontSize: 20,
        position: 'rt',  // possible values are 'lft', 'rt', 'top', 'bot'
        offset: [-20, 20]   // (in pixels)
      }
      });
let yaxis = board1.create('axis', [[0, 0], [0, 1]], 
      {name:'y', 
      withLabel: true, 
      label: {
        fontSize: 20,
        position: 'rt',  // possible values are 'lft', 'rt', 'top', 'bot'
        offset: [-30, -20]   // (in pixels)
        }
      });   

// parabala and it's derivative
let f = function(x) { return  x*x; };
let df = function(x) { return 2*x; };
let x = board1.create('glider', [1,0, xaxis], {name:'x', fixed:true, size:6});
let fx = board1.create('point', [
  function() { return x.X(); }, 
  function() { return f(x.X()); }], {name:'', color:'#222299', fixed:true});
let graph_f = board1.create('functiongraph', [f,-10,10], {strokeColor:'#999999'});
let graph_df = board1.create('functiongraph', [df,-10,10], {strokeColor:'#44AA44', visible:false});
let dfx = board1.create('point', [
  function() { return x.X(); }, 
  function() { return df(x.X()); }], {name:'', color:'#44AA44', fixed:true, visible:false});


// Secant line section
// the slider point for the secant
let x_h = board1.create('glider', [x.X() + 2, 0, xaxis], {name:'x + h', size:6, color:'green', visible:true} ); 

// sliding point on parabala 
let fx_h = board1.create('point', [
                function() { return x_h.X(); }, 
                function() { return f(x_h.X()); }
          ], {name:'', color:'#222299', fixed: true, size:3, visible:true});

let secant = board1.create('line', [fx, fx_h], {color:'#222299', visible:true});
let secantSlope = function() { 
  if (x.X() == x_h.X()) { return "UNDEFINED: divide by zero"; }
  return ((f(x.X()) - f(x_h.X()))/(x.X() - x_h.X())).toFixed(3).toString(); 
}

let secantSlopeText = board1.create('text',[
  function() { return x.X() + (x_h.X() - x.X())/2 - 1.8; },
  function() { return f(x.X()) + (f(x_h.X()) - f(x.X()))/2;},
  function(){ return 'slope = '+ secantSlope(); }], {fontSize:15, visible:true});

let p = board1.create('point', [ 
  function() { return x_h.X(); }, 
  function() { return f(x.X());}], {visible:false});

let triangle = board1.create('polygon', [fx, fx_h, p], {
  fillColor:'#33FFFF', 
  fillOpacity: 50,
  borders: {strokeColor: 'yellow'}, 
  strokeWidth:3, visible:false});

let rise = board1.create('line', [fx_h, p], {color:'black', strokeWidth:1, straightFirst:false, straightLast:false, dash:2, visible:true});
let run = board1.create('line', [fx, p], {color:'black', strokeWidth:1, straightFirst:false, straightLast:false, dash:2, visible:true});
let riseText = board1.create('text', [
  function() { if (x_h.X() > x.X()) { return x_h.X() + 0.1; } 
         return x_h.X() - 1.5; },
  function() { return (f(x_h.X()) - f(x.X()))/2 + f(x.X()); },
  '(x+h)^2 - x^2'], {fontSize:12, visible:false});

let runText = board1.create('text', [
  function() { return x.X() + (x_h.X() - x.X())/2; },
  function() { return f(x.X()) - 0.1; },
  'h'], {fontSize:12, visible:false});


let triangleOn = function() {
  triangle.setAttribute({visible:true});
  riseText.setAttribute({visible:true});
  runText.setAttribute({visible:true});
};

let triangleOff = function() {
  triangle.setAttribute({visible:false});
  riseText.setAttribute({visible:false});
  runText.setAttribute({visible:false});
};

window.triangleOff = triangleOff;
window.triangleOn  = triangleOn;

let runLimit = function() {
  x_h.moveTo([x.X(),0],2000);
}

let resetSecant = function() {
  x.moveTo([1,0]);
  x_h.moveTo([3,0]);
};

window.runLimit = runLimit;
window.resetSecant = resetSecant;

this.sizeChanged = function() {      
  board1.resizeContainer(myDiv.offsetWidth, myDiv.offsetHeight);
};

 
```
#### --outlinebox

#### --outlinebox right2
The definition of the derivative starts with the **slope** of a secant line. 
$$\frac{(x + h)^2 - x^2}{h}$$

To find the derivative $f'(x)$, we take the limit of the slope of the secant line as $h$ goes to zero.
$$f'(x) = \lim_{h \to 0} \frac{(x + h)^2 - x^2}{h}$$

You can investigate what happens when $h$ gets very small by dragging the green dot towards the red dot or by using these buttons. [Send h to zero](:=run=true) [Reset](:=reset=true)

**What happens when $h=0$?**
- The slope of the secant line is undefined when $h=0$.

**What happens as $h$ gets very close to $0$?**
- The secant line gets closer and closer to the **tangent** line.  
- The slope of the secant line gets closer and closer to 2.
#### --outlinebox
#### --outlinebox


### Solving the Limit 
To solve the limit and find a function for the derivative we need to do some algebra.
$$
\begin{align}
f'(x) = \lim_{h \to 0} \frac{(x + h)^2 - x^2}{h} & = \lim_{h \to 0} \frac{x^2 + 2hx + h^2 - x^2}{h}  & \textrm{expand $(x+h)^2$} \newline 
& = \lim_{h \to 0} \frac{2hx + h^2}{h} & \textrm{combine like terms}  \newline
& = \lim_{h \to 0} 2x + h & \textrm{cancel $h$ terms}  \newline
& = 2x  
\end{align}
$$
```javascript /autoplay
const outer = document.getElementById('outer2');
const left = document.getElementById('left2');
const right = document.getElementById('right2');

outer.classList.remove('decoration-outlinebox');
left.classList.remove('decoration-outlinebox');
right.classList.remove('decoration-outlinebox');

outer.classList.add('outer');
left.classList.add('left');
right.classList.add('right');

const math4 = document.getElementById('MathJax-Element-4-Frame');
math4.onmouseover = logMouseOver3;
math4.onmouseout = logMouseOut3;
math4.classList.add('highlightOff');

function logMouseOver3() {
  math4.classList.remove('highlightOff');
  math4.classList.add('highlightOn');
  window.triangleOn();
}

function logMouseOut3() {
  math4.classList.remove('highlightOn');
  math4.classList.add('highlightOff');
  triangleOff();
}

smartdown.setVariable('run', false);
smartdown.setVariable('reset', false);
this.dependOn = ['run', 'reset'];
this.depend = function() {
  if (env.run == true) {
    smartdown.setVariable('run',false);
    window.runLimit();
  }
  if (env.reset == true) {
    smartdown.setVariable('reset', false);
    window.resetSecant();
  }
};

```


#### --outlinebox outer3

#### --outlinebox left3

```javascript /playable/autoplay
//smartdown.import=https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraphcore.js

smartdown.importCssUrl('https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraph.css');
myDiv = this.div;

myDiv.innerHTML = `<div id='box3' class='jxgbox' style='height:500px'>`;


JXG.Options.axis.ticks.majorHeight = 40;
// create the board
board2 = JXG.JSXGraph.initBoard('box3', {boundingbox:[-5,10,5,-3], showCopyright:false, keepaspectratio:false, axis:false});
board2.resizeContainer(myDiv.offsetWidth, myDiv.offsetHeight);

let xaxis = board2.create('axis', [[0, 0], [1,0]], 
      {name:'x', 
      withLabel: true,
      label: {
        fontSize: 20,
        position: 'rt',  // possible values are 'lft', 'rt', 'top', 'bot'
        offset: [-20, 20]   // (in pixels)
      }
      });
let yaxis = board2.create('axis', [[0, 0], [0, 1]], 
      {name:'y', 
      withLabel: true, 
      label: {
        fontSize: 20,
        position: 'rt',  // possible values are 'lft', 'rt', 'top', 'bot'
        offset: [-30, -20]   // (in pixels)
        }
      });   

// parabala and it's derivative
let f = function(x) { return  x*x; };
let df = function(x) { return 2*x; }
let x = board2.create('glider', [2,0, xaxis], {name:'x', size:6});
let fx = board2.create('point', [
  function() { return x.X(); }, 
  function() { return f(x.X()); }], {name:'', color:'#222299', fixed:true});
let graph_f = board2.create('functiongraph', [f,-10,10], {strokeColor:'#999999'});
let graph_df = board2.create('functiongraph', [df,-10,10], {strokeColor:'#44AA44', visible:true});
let dfx = board2.create('point', [
  function() { return x.X(); }, 
  function() { return df(x.X()); }], {name:'', color:'#44AA44', fixed:true, visible:true});

// tangent line section
let tangent = board2.create('line', [
  function() { return f(x.X());},
  function() { return - df(x.X());},
  1], {color:'#222299', visible:true});
let tangentSlopeText = board2.create('text',[
  function() { return x.X() + 0.5; },
  function() { return f(x.X()) + 0.5;},
  function(){ return 'slope = '+ df(x.X()).toFixed(2); }], {fontSize:15, visible:true});


// Secant line section
// the slider point for the secant
let x_h = board2.create('glider', [x.X() + 3, 0, xaxis], {name:'x + h', size:6, color:'green', visible:false} ); 

// let highlightFon = function() {
//   graph_f.setAttribute({strokeColor:'#33FFFF', strokeWidth:3});
// };

// let highlightFoff = function() {
//   graph_f.setAttribute({strokeColor:'#999999', strokeWidth:1});
// };

// window.highlightFoff = highlightFoff;
// window.highlightFon = highlightFon;

this.sizeChanged = function() {      
  board2.resizeContainer(myDiv.offsetWidth, myDiv.offsetHeight);
};

 
```
#### --outlinebox


#### --outlinebox right3

We write this as
$$f'(x) = \lim_{h \to 0} 2x + h = 2x$$
The derivative of $f(x) = x^2$ is the function
$$f'(x) = 2x$$

#### --outlinebox
#### --outlinebox


```javascript /autoplay

const outer = document.getElementById('outer3');
const left = document.getElementById('left3');
const right = document.getElementById('right3');

outer.classList.remove('decoration-outlinebox');
left.classList.remove('decoration-outlinebox');
right.classList.remove('decoration-outlinebox');

outer.classList.add('outer');
left.classList.add('left');
right.classList.add('right');



```

