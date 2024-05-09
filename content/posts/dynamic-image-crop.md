---
title: 'Dynamic Image Cropping in Storyline 360 with Javascript & GSAP'
date: 2024-04-14
draft: false
---

In this video tutorial, we find out how to use CSS clip path to change the shape of our images, or rather of our image cropping areas, in Articulate Storyline 360.

We're going to use Execute Javascript triggers, and, inside them, our code will add clip paths to the pictures. Then, we'll animate those clip paths with the GSAP (Greensock Animation Platform) in order to create a nice effect.

Although there already are some features available that achieve more or less the same thing in Storyline, it's interesting to see how we can control our animation using Javascript.


Find out more about clip paths here:
https://developer.mozilla.org/en-US/docs/Web/CSS/clip-path

CSS clip path generator:
https://10015.io/tools/css-clip-path-generator


## Here's the video
{{< youtube Fu2pNHoKX90 >}}

## Code used

Clip with circle

```js {linenos=true}
var picture = document.querySelector("[data-acc-text='picture']");

// Add clip path to the selected element
picture.style.clipPath = 'circle(100%)';

// Animate the clip path
gsap.to(picture, {
  duration: 3,
  clipPath: 'circle(0%)'
});


```

That's all, folks!

```js {linenos=true}
var picture = document.querySelector("[data-acc-text='picture']");
var character = document.querySelector("[data-acc-text='character']");
var endText = document.querySelector("[data-acc-text='endText']");

// Add clip path to the selected element
picture.style.clipPath = 'circle(100%)';


gsap.set(character, {opacity:0, scale:0});
gsap.set(endText, {opacity:0, scale:0});


let timeline = gsap.timeline({paused:true});
// Animate the clip path

timeline.to(picture, {duration: 3, clipPath: 'circle(30%)', ease:"power1.out"});
timeline.to(character, {duration: 1, scale:1, opacity:1, ease:"elastic.out" });
timeline.to(endText, {duration:2, scale:1, opacity:1, ease:"elastic.inOut"});
timeline.to(endText, {duration: 1, scale:0, opacity:0, ease:"power1.out"}, "+=1");
timeline.to(character, {duration: 1, scale:0, opacity:0, ease:"power1.out"}, "<");
timeline.to(picture, {duration: 1, clipPath: 'circle(0%)', ease:"power1.out"}, "<");


picture.addEventListener('click', () => {
    timeline.play();
});

```