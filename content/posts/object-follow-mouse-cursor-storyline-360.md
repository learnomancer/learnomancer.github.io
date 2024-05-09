---
title: 'Make Objects Follow Your Mouse Cursor in Storyline 360 with JavaScript & GSAP'
date: 2024-02-26
draft: false
---

In this video tutorial, we will use Javascript and a bit of GSAP to make an Articulate Storyline 360 slide object follow the mouse cursor's position.

We will use getBoundingClientRect() to get the position of our slide in the viewport, then make sure the satellite moves only when the mouse is within the bounds of the slide.

## Here's the video
{{< youtube V8j7KfkasDY >}}

## Code used

```js {linenos=true}
var player = GetPlayer();
var satellite = document.querySelector("[data-acc-text='satellite']");

var offsetX = 30;
var offsetY = 30;

//this will execute each time we move the mouse
document.addEventListener('mousemove', function(event){


    //select the slide
    var slide = document.getElementById('slide');

    //find out what distance it is from the edges of the viewport
    var slideRect = slide.getBoundingClientRect();

    //declare two variables, and use them to store the position of the mouse
    var mouseX = event.clientX;
    var mouseY = event.clientY;



    //check if the mouse is moving ONLY within the slide
    if(mouseX >= slideRect.left &&     mouseX <= slideRect.right &&        mouseY >= slideRect.top &&        mouseY <= slideRect.bottom   ){

    //adjust the coordinates based on the position and size of the slide
    var adjustedX = mouseX - slideRect.left + offsetX;
    var adjustedY = mouseY - slideRect.top + offsetY;


    //ensure that the mouse doesn't go beyond the right and bottom edge of the slide
    adjustedX = Math.max(0, Math.min(slideRect.right, adjustedX));
    adjustedY = Math.max(0, Math.min(slideRect.bottom, adjustedY));


    //setting the text variables so we can see them update in storyline
    player.SetVar("SL_mouseX", adjustedX);
    player.SetVar("SL_mouseY", adjustedY);

    //animate the satellite
    gsap.to(satellite, {x:adjustedX, y:adjustedY});
    };

});

```