---
title: 'I cloned a sheep in Articulate Storyline 360'
date: 2024-04-07
draft: false
---

In this video tutorial, we use the cloneNode function of Javascript to clone a png image of a sheep. And then we'll move the clones using GSAP to create a nice division animation.

It was amazing to see that you can actually duplicate elements in Articulate Storyline 360 using Javascript.

I was inspired by Doctor Strange splitting into multiple clones during the battle with Thanos from Infinity War (lol), and I wondered if we could achieve this effect in Articulate Storyline 360.

Check out the documentation for the cloneNode function here:
https://developer.mozilla.org/en-US/docs/Web/API/Node/cloneNode

## Here's the video
{{< youtube szph_kpxjzA >}}

## Code used

```js {linenos=true}

var sheep = document.querySelector("[data-acc-text='sheep']");

// Function to execute when the button is clicked
function cloneElement(target, numClones) {
    // Calculate the step size based on the number of clones
    const step = 400 / (numClones - 1); // Total range is 400 (-200 to 200)

    for (let i = 0; i < numClones; i++) {
        // Clone the image
        const clone = target.cloneNode(true);

        // Append clones to the container
        target.parentElement.appendChild(clone);

        // Calculate the xPercent value for each clone
        const xPercent = -200 + step * i;

        // Animate each clone
        gsap.to(clone, { xPercent: xPercent, duration: 1, opacity: 1, ease: 'power2.out' });
    }
}

// Add event listener to the image
sheep.addEventListener('click', () => {
    cloneElement(sheep, 4); // Create 4 clones
    sheep.remove();
});

```