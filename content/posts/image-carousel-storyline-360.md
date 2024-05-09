---
title: 'Create an image carousel in Articulate Storyline 360'
date: 2024-03-06
draft: false
---

In this video tutorial, we will explore how to create an image carousel interaction in Articulate Storyline 360 in several different ways.

We will use motion paths to move the image carousel when the user presses some buttons, then use Storyline triggers to check for intersection and intersection end in order to clamp the movement of our carousel by hiding the buttons.

Then, we will explore how to clamp the movement of an image carousel when we use GSAP to animate it. We will use the gsap.getProperty function to get the position of the carousel on the X axis, then use an if statement to check if it is greater or lesser than some limits we set. That way, even if the user presses a button, once the carousel reaches or exceeds that limit, the movement will not trigger.

Then, we will explore how the user can control the same interaction by hovering over some buttons, which will cause the carousel to move to a specific position depending on which button the mouse hovers over.

## Here's the video
{{< youtube LRFColrKS-k >}}

## Code used

```js {linenos=true}

//if button_forward is pressed
var animationTarget = document.querySelector("[data-acc-text='group_1']");

var currentX = gsap.getProperty(animationTarget, "xPercent");
var forwardLimit = -40;

console.log("before animation starts " + currentX);

if(currentX > forwardLimit) {
    gsap.to(animationTarget, {
        duration:2,
        xPercent:"-=" + 10,
        onComplete:function(){
            currentX = gsap.getProperty(animationTarget, "xPercent");
            console.log("on animation complete " + currentX);
        }
    });
}

```

```js {linenos=true}
//if button_back is pressed

var animationTarget = document.querySelector("[data-acc-text='group_1']");

var currentX = gsap.getProperty(animationTarget, "xPercent");
var backLimit = 35;

console.log("before animation starts " + currentX);

if(currentX < backLimit) {
    gsap.to(animationTarget, {
        duration:2,
        xPercent:"+=" + 10,
        onComplete:function(){
            currentX = gsap.getProperty(animationTarget, "xPercent");
            console.log("on animation complete " + currentX);
        }
    });
}

```

```js {linenos=true}

var animationTarget = document.querySelector("[data-acc-text='group_1']");
var player = GetPlayer();
var currentImageHover = player.GetVar("currentImageHover");
var xPosition;

switch(currentImageHover){
    case 1:
        xPosition = 340;
        gsap.to(animationTarget, {duration:2, x:xPosition});
        break;
    case 2:
        xPosition = -446;
        gsap.to(animationTarget, {duration:2, x:xPosition});
        break;
    case 3:
        xPosition = -1160;
        gsap.to(animationTarget, {duration:2, x:xPosition});
        break;
    case 4:
        xPosition = -2009;
        gsap.to(animationTarget, {duration:2, x:xPosition});
        break;
    case 5:
        xPosition = -2790;
        gsap.to(animationTarget, {duration:2, x:xPosition});
        break;
    
}

```