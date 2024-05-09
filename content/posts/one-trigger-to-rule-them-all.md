---
title: 'Animate Multiple Elements with One Trigger across your Storyline 360 Project using Javascript'
date: 2024-05-05
draft: false
---

Learn how to apply animations across your eLearning project with just one Execute Javascript trigger!

No Format Painter! No going back to tediously apply animations or states manually.

In this video tutorial, I'll guide you through the steps to apply hover animations to multiple elements in your Storyline projects using a single master slide trigger.

This method is perfect for large projects with varied interactive components, ensuring uniformity and saving you tons of time. We'll cover how to use JavaScript and GSAP to create engaging, responsive animations that enhance user interactions. 

## Here's the video
{{< youtube O0jIS0O_UN0 >}}

## Code used

#### Adding movement

```js {linenos=true}
document.querySelectorAll("[data-acc-text='interactable']").forEach(element => {
    // Create a new timeline for each element, paused initially
    let tl = gsap.timeline({ paused: true });


    // Define the animation for this specific element
    tl.to(element, { yPercent: -10, duration: 0.3 });


    // Set up event listeners for this element
    element.addEventListener('mouseenter', () => {
        tl.play();
    });


    element.addEventListener('mouseleave', () => {
        tl.reverse();
    });
});
```

#### Change to hand cursor
```js {linenos=true}
    element.addEventListener('mouseenter', () => {
        element.style.cursor = 'pointer';
      	tl.play();
    });


    element.addEventListener('mouseleave', () => {
        element.style.cursor = '';
      	tl.reverse();
    });

```