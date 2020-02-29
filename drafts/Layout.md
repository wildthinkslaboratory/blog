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
  function() { return f(x.X()); }], {name:'', color:'blue', fixed:true});
let graph_f = board0.create('functiongraph', [f,-10,10], {strokeColor:'#999999'});
let graph_df = board0.create('functiongraph', [df,-10,10], {strokeColor:'#44AA44', visible:false});
let dfx = board0.create('point', [
  function() { return x.X(); }, 
  function() { return df(x.X()); }], {name:'', color:'#44AA44', fixed:true, visible:false});

// tangent line section
let tangent = board0.create('line', [
  function() { return f(x.X());},
  function() { return - df(x.X());},
  1], {visible:true});
let tangentSlopeText = board0.create('text',[
  function() { return x.X() + 0.5; },
  function() { return f(x.X()) + 0.5;},
  function(){ return 'slope = '+ df(x.X()).toFixed(2); }], {fontSize:15, visible:true});


// Secant line section
// the slider point for the secant
let x_h = board0.create('glider', [x.X() + 3, 0, xaxis], {name:'x + h', size:6, color:'green', visible:false} ); 



this.sizeChanged = function() {      
  board0.resizeContainer(myDiv.offsetWidth, myDiv.offsetHeight);
};

 
```
#### --outlinebox


#### --outlinebox right1

### Finding the Derivative
We want to find a function that tells us the **slope** of the tangent line for the function $f(x)=x^2$. Drag the red dot to see the slope of the tangent line for different values of $x$.

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

@media (min-width: 800px) {
  .outer {
   
  }

  .left {
    width: 58%;
    display: inline-block;
    vertical-align: top;
  }

  .right {
    width: 40%;
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

```



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
let x = board1.create('glider', [1,0, xaxis], {name:'x', size:6});
let fx = board1.create('point', [
  function() { return x.X(); }, 
  function() { return f(x.X()); }], {name:'', color:'blue', fixed:true});
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
          ], {name:'', color: 'blue', fixed: true, size:3, visible:true});

let secant = board1.create('line', [fx, fx_h], {strokeColor:'blue', visible:true});
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

let rise = board1.create('line', [fx_h, p], {color:'black', strokeWidth:1, straightFirst:false, straightLast:false, dash:2, visible:true});
let run = board1.create('line', [fx, p], {color:'black', strokeWidth:1, straightFirst:false, straightLast:false, dash:2, visible:true});
let riseText = board1.create('text', [
  function() { if (x_h.X() > x.X()) { return x_h.X() + 0.1; } 
         return x_h.X() - 1.5; },
  function() { return (f(x_h.X()) - f(x.X()))/2 + f(x.X()); },
  '(x+h)^2 - x^2'], {fontSize:12, visible:true});

let runText = board1.create('text', [
  function() { return x.X() + (x_h.X() - x.X())/2; },
  function() { return f(x.X()) - 0.3; },
  'h'], {fontSize:12, visible:true});




this.sizeChanged = function() {      
  board1.resizeContainer(myDiv.offsetWidth, myDiv.offsetHeight);
};

 
```
#### --outlinebox


#### --outlinebox right2

### Derivatives are Slopes
The derivative definition starts with the **slope** of a secant line. See if you can understand why this expression describes the slope by looking at the picture.
$$\frac{(x + h)^2 - x^2}{h}$$
Now we do some algebra.
$$
\begin{align}
\frac{(x + h)^2 - x^2}{h} &  & \textrm{expand $(x+h)^2$} \newline 
\frac{x^2 + 2hx + h^2 - x^2}{h} &  & \textrm{combine like terms}  \newline
\frac{2hx + h^2}{h}  &  & \textrm{cancel $h$ terms}   \newline
2x + h &
\end{align}
$$
The expression $2x + h$ represents the **slope** of the secant line for all values of $x$ and $h$.

#### --outlinebox
#### --outlinebox


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

```


#### --outlinebox outer3

#### --outlinebox left3

```javascript /playable/autoplay
//smartdown.import=https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraphcore.js

smartdown.importCssUrl('https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraph.css');

const myDiv = this.div;
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
let df = function(x) { return 2*x; };
let x = board2.create('glider', [1,0, xaxis], {name:'x', size:6});
let fx = board2.create('point', [
  function() { return x.X(); }, 
  function() { return f(x.X()); }], {name:'', color:'blue', fixed:true});
let graph_f = board2.create('functiongraph', [f,-10,10], {strokeColor:'#999999'});
let graph_df = board2.create('functiongraph', [df,-10,10], {strokeColor:'#44AA44', visible:false});
let dfx = board2.create('point', [
  function() { return x.X(); }, 
  function() { return df(x.X()); }], {name:'', color:'#44AA44', fixed:true, visible:false});


// Secant line section
// the slider point for the secant
let x_h = board2.create('glider', [x.X() + 2, 0, xaxis], {name:'x + h', size:6, color:'green', visible:true} ); 

// sliding point on parabala 
let fx_h = board2.create('point', [
                function() { return x_h.X(); }, 
                function() { return f(x_h.X()); }
          ], {name:'', color: 'blue', fixed: true, size:3, visible:true});

let secant = board2.create('line', [fx, fx_h], {strokeColor:'blue', visible:true});
let secantSlope = function() { 
  if (x.X() == x_h.X()) { return "UNDEFINED: divide by zero"; }
  return ((f(x.X()) - f(x_h.X()))/(x.X() - x_h.X())).toFixed(3).toString(); 
}

let secantSlopeText = board2.create('text',[
  function() { return x.X() + (x_h.X() - x.X())/2 - 1.8; },
  function() { return f(x.X()) + (f(x_h.X()) - f(x.X()))/2;},
  function(){ return 'slope = '+ secantSlope(); }], {fontSize:15, visible:true});

let p = board2.create('point', [ 
  function() { return x_h.X(); }, 
  function() { return f(x.X());}], {visible:false});

let rise = board2.create('line', [fx_h, p], {color:'black', strokeWidth:1, straightFirst:false, straightLast:false, dash:2, visible:true});
let run = board2.create('line', [fx, p], {color:'black', strokeWidth:1, straightFirst:false, straightLast:false, dash:2, visible:true});
let riseText = board2.create('text', [
  function() { if (x_h.X() > x.X()) { return x_h.X() + 0.1; } 
         return x_h.X() - 1.5; },
  function() { return (f(x_h.X()) - f(x.X()))/2 + f(x.X()); },
  '(x+h)^2 - x^2'], {fontSize:12, visible:true});

let runText = board2.create('text', [
  function() { return x.X() + (x_h.X() - x.X())/2; },
  function() { return f(x.X()) - 0.3; },
  'h'], {fontSize:12, visible:true});




this.sizeChanged = function() {      
  board2.resizeContainer(myDiv.offsetWidth, myDiv.offsetHeight);
};

 
```
#### --outlinebox


#### --outlinebox right3

### Use the Limit to Turn the Secant into a Tangent
We can use a **limit** to turn a secant into a tangent. If we drag the green dot $x+h$  towards the red $x$ dot 
- the value of $h$ gets very small.
- the secant gets closer to the tangent 
- the slope of the secant $2x + h$ gets close to $2x$.

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

