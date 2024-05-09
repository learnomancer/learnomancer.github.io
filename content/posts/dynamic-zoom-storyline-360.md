---
title: 'Dynamic Zoom Effects in Storyline 360 using Javascript & GSAP'
date: 2024-02-27
draft: false
---

In this video tutorial, we'll explore how we can zoom in Articulate Storyline 360 by analyzing the options available when using the default way - zoom regions.

Then, we will explore how to use GSAP to achieve a similar effect by modifying an object's scale.

We will then control our zoom with buttons that allow us to zoom in and zoom back out to reset the view. And we'll also control our zoomed in image using arrow buttons.

Hope you enjoy these tips and tricks. 🙂

## Here's the video
{{< youtube YCi8--e-dyk >}}

## Code used

```js {linenos=true}
//reset

var animationTarget = document.querySelector("[data-acc-text='myGroup']");

gsap.to(animationTarget, {scale:1, xPercent:0, yPercent:0})

```

```js {linenos=true}
//zoom in

var animationTarget = document.querySelector("[data-acc-text='myGroup']");

gsap.to(animationTarget, {scale:2,transformOrigin:"center left", duration: 5 })

```

```js {linenos=true}

//move down

var animationTarget = document.querySelector("[data-acc-text='myGroup']");

gsap.to(animationTarget, {yPercent:"-=3"})

```