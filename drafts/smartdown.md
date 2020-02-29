---
layout: post
title: You Can Do It! How to Write Interactive Web Content
date: 2020-02-14
smartdown: true
comments: false
---

### Changing the way we communicate

The printing press revolutionized communication, causing an explosion in literacy and the exchange of ideas. and Innovation followed, leading the
 Telegraph, Movies, Internet.

The way we communicate continues to evolve. 

If you know how to add pictures, videos and hyperlinks to your blog posts and web pages, then you're ready for the next step.


Easy ways to make your content more interactive.


Web publishing tools. Smartdown, Idyll, p5js d3 graphjsx make building bite sized apps 

### Test Map

```javascript /playable/autoplay
var myDiv = this.div;

var mymap="https://drive.google.com/open?id=1m4pLLHLjzrSWITSY2TY68_PFcV-1yqo8&usp=sharing"


```


### What does the Revolution Look Like? 


	- What if you could express it like the idea shared in *Parable of the Polygons*.  What if you could create that kind of an experience for your reader.  



[The Pudding](https://pudding.cool)
[Explorable Explanations](https://explorabl.es)


Many large online publications are including data journalism.  Many behind pay walls.
[Data Journalism](https://en.wikipedia.org/wiki/Data_journalism)
[FiveThirtyEight](https://fivethirtyeight.com)
[The Guardian Data Blog](https://www.theguardian.com/media/data-journalism)


Processing
[Processing Foundation](https://processingfoundation.org)
Tools for Artists, Scientitsts, Educators, curious creative everyday people.

[Open Processing](https://www.openprocessing.org)



### Progressive Disclosure

[Progressive Disclosure](https://en.wikipedia.org/wiki/Progressive_disclosure) is a communication strategy that maintains the user's attention by reducing clutter.  The most important information is presented visually first. Secondary information, such as low level details, side notes, definitions and references to related material can be revealed if the user chooses and then tucked away again when they are not needed. 

In this example, the bio for Alan Turing is tucked away in a smartdown [tooltip](https://smartdown.site/#gallery/Disclosables.md).  The bio is revealed when the mouse hovers of the text of his name.

# --colorbox cb1
The Turing machine, is a mathematical model for computation.  Invented by [Alan Turing](::turing/tooltip)  in 1936, this simple model is powerful enough to capture all aspects of modern computers and has led to unexpected insights into the limitations of all forms computation.
# --colorbox

# :::: turing
**Alan Turing** was a mathematician and a founder of the field of computer science.  His work on Turing machines is the basis of theoretical computer science.  During World War II, Turing played a critical role in the work of decrypting messages encoded on the Enigma machine, allowing the Allied forces to defeat the Nazis in many engagements. [Learn More](https://en.wikipedia.org/wiki/Alan_Turing)
# ::::

Both of these examples were created using smartdown [disclosables](https://smartdown.site/#gallery/Disclosables.md).  They are one of the easiest things to use in smartdown and don't require and knowledge of javascript, html or web development.

### Adding Cells.

# Mad Lib Time
[name](:?NAM)
[animal](:?AN)
[direction](:?DIR)
[area](:?PLA)
[weather](:?WE)
[anoying dog](:?DO)
[poison](:?PO)
[song](:?SO)
[loud volume](:?VO)
[destructive obgect](:?DEOB)
[food](:?FOO)
[number biger than 3](:?NUM)

## [Mad Lib](::madli)

# :::: madli

[](:!NAM) was a young [](:!AN) who lived just [](:!DIR) of [](:!PLA). it would always [](:!WE) on his property. but as soon as he left his property the [](:!WE) would stop. [](:!NAM) lived with a dog named [](:!DO) whos farts were so awful it would be beter if he just farted [](:!PO). One day the stareo started blasting [](:!SO) at [](:!VO), sudenly a [](:!DEOB) crashed through the wall with a plate of [](:!FOO)s sitting on top of it. [](:!DO) quickly ate every single [](:!FOO) before letting out the biggest fart he had ever farted. he farted so hard he was sent to  the [](:!NUM)th demention.

# ::::


### Adding Apps



### Conclusion

I can't imagine writing in pure text ever again.




### Data Science Journalism

### Explorable Explanations

It doesn't tell you content, it gives you an interactive way to discover it.

### Parable of the Polygons
![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1f/Parable_of_the_Polygons_Meh_characters.svg/320px-Parable_of_the_Polygons_Meh_characters.svg.png)

[Parable of the Polygons](https://ncase.me/polygons/) Has implications for policy.



### Putting it all together

### Asking Readers Questions

Two disclosables, cell, decoration to make it pretty.  held together by a little hidden inline app. 6 lines of code.

Here is a cool example where two disclosables are combined to create an interactive math problem for the user.  The first disclosable allows the user to get a hint about how to answer the question.  In this case the hint is a bit overly generous in case its been a while since you've taken algebra.  The second disclosable will appear after the correct answer has been entered to give the user a celebratory high five.

#### --partialborder problem1

**Problem 1.3**

For what real values of $c$ is $x^2 + 16x + c$ the square of a binomial? If you find more than one, then list your values separated by commas.

[Your Answer](:?answer)

```javascript /autoplay
smartdown.setVariable('answer', '');
this.dependOn = ['answer'];

this.depend = function() {
  if (env.answer === '64') {
    smartdown.showDisclosure('highfive', '', 'bottomright,transparent');
    setTimeout(function () {
      smartdown.hideDisclosure('highfive','','bottomright,transparent');
    }, 3000);
  }
};
```
[Hint](::get_hint)

# :::: get_hint
The answer is 64.
# ::::

#### --partialborder


# :::: highfive
# --colorbox
High five! :raised_hand:
# --colorbox
# ::::



### For Good or Evil

It's a new way to write.  More choices.  You can make things worse before you make them better.



