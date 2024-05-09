---
title: 'Dynamic Progress Bar for Any Number of Slides in Storyline 360 using Javascript'
date: 2024-03-18
draft: false
---

In this video tutorial, we will explore how to make a progress bar in Articulate Storyline 360.

Our progress bar will update when we move back and forward through our slides. And, no matter how many slides we have in our project, our progress bar will scale and display the progress accurately.

The progress bar uses Javascript (GSAP) to animate the shape and makes use of the built-in Storyline variables showing the slide number in the project (Project.SlideNumber) or the slide number in the scene (Scene.SlideNumber).

We will also be able to make individual progress bar for each of our scenes, which will display only how we progress through the slides of that certain scene.

## Here's the video
{{< youtube dJ0GHzbbUXU >}}

## Code used

```js {linenos=true}
var progressBar = document.querySelector("[data-acc-text='progressBar']");
var progressBar_scene = document.querySelector("[data-acc-text='progressBar_scene']");

var player = GetPlayer();
var JS_totalSlidesInProject = player.GetVar("SL_totalSlidesInProject");
var JS_currentSlide = player.GetVar("SL_currentSlide");

var JS_totalSlidesInScene = player.GetVar("SL_totalSlidesInScene");
var JS_currentSlideInScene = player.GetVar("SL_currentSlideInScene");

var objectScale = (JS_currentSlide / JS_totalSlidesInProject) * 1;

var objectScale_scene = (JS_currentSlideInScene / JS_totalSlidesInScene) * 1;


gsap.set(progressBar, {scaleX:objectScale, transformOrigin:"center left"});


gsap.set(progressBar_scene, {scaleX:objectScale_scene, transformOrigin:"center left"});

```