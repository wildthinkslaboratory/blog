---
layout: post
title: Product Rule Exploration
date: 2020-01-01
smartdown: true
comments: false
---

### To Do
- convert the calc lib to export classes
- create a DisplaySecant or add attributes to regular Adj Secant
- rewrite Layout post with new Secant?
- make three boxes with three functions and three secants
- sync their Xintervals. Can they share?  Or should they be synched from outside?
- make a standardized method for window height


### Product Rule Exploration
This is where some text will go. This is where some text will go. This is where some text will go. This is where some text will go. This is where some text will go. This is where some text will go. This is where some text will go. This is where some text will go.

```javascript /playable/autoplay
//smartdown.import=https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraphcore.js

smartdown.importCssUrl('https://cdnjs.cloudflare.com/ajax/libs/jsxgraph/0.99.7/jsxgraph.css');

// import the calc library
//smartdown.import=/smartblog/assets/calc.js

const myDiv = this.div;
myDiv.style.width = '100%';
myDiv.style.height = '60%';
myDiv.style.margin = 'auto';
myDiv.innerHTML = `<div id='box1' style='height:500px'></div>`;

let div1Width = 1;
let div1Height = 0.8;

let xlow = -2;
let xhigh = 10;
let ylow = -2;
let yhigh = 10;

let f = function(x) { return 1 / x; };
let sfboard = new SingleFunctionBoard('box1', 
  [xlow, yhigh, xhigh, ylow], 
  f,
  { xName: 'x', yName: 'y', startX:xlow, endX:xhigh });


let workspace = new WorkSpace(sfboard.board);
//workspace.addElement(1, 0.25, f);
let xint = new XInterval(sfboard.board, 3,5);
let binfo = new BoardInfo(sfboard.board);

////////////////////////////////////////////////////////////////////////////////////
// Here is where you configure the workspace based on what elements you want to 
// add.  


// ////////////////////////////////////////////////////////////////////////////////////

this.sizeChanged = function() {
  workspace.resize(myDiv.offsetWidth, myDiv.offsetHeight);       
};

sfboard.board.on('update', function() {
  workspace.boardUpdate();              // hook up workspace update functions
});


```