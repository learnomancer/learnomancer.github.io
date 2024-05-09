---
title: 'Storyline 360 Crash Course on animation and interactivity using GSAP & Javascript'
date: 2024-02-18
draft: false
---

In this video tutorial, we'll go through a few projects that will help us understand how to implement GSAP to create complex animations, emphasis animations and enhanced interactions in Articulate Storyline 360.

GSAP (Greensock Animation Platform) is a Javascript code library that is already integrated into Storyline, which makes it easier for us to animate our slide objects with code to increase interactivity and perhaps cut down on development time for our e-learning projects.

This should be an interesting topic for intermediate to advance elearning developers using Storyline.

## Here's the video
{{< youtube 7Zm-rjApatM >}}

## Code used


#### 1 - Car

```js {linenos=true}

var animationTarget = document.querySelector("[data-acc-text='car']");

gsap.to(animationTarget, { 
    x: "+=100",
    duration:2,
    ease: "elastic.inOut(1,0.3)",
    scale:2
  });
```

#### 2 - Astronaut

```js {linenos=true}

var elementToAnimate= document.querySelector("[data-acc-text='astronaut']");


gsap.to(elementToAnimate, {
    repeat:-1,
    yoyo:true, 
    duration: 2,
    ease: "power1.inOut",
    yPercent: -5 
});

```

#### 3 - Ghost

```js {linenos=true}

var elementToAnimate= document.querySelector("[data-acc-text='ghost']");


gsap.to(elementToAnimate, {
    opacity:0,
    duration:2
});

var player = GetPlayer();
var currentGhostOpacity = player.GetVar("SL_currentGhostOpacity");
var currentGhostOpacity = player.SetVar("SL_currentGhostOpacity",0);

```

```js {linenos=true}

var elementToAnimate= document.querySelector("[data-acc-text='ghost']");


gsap.to(elementToAnimate, {
    opacity:1,
    duration:2
});

var player = GetPlayer();
var currentGhostOpacity = player.GetVar("SL_currentGhostOpacity");
var currentGhostOpacity = player.SetVar("SL_currentGhostOpacity",100);

```



```js {linenos=true}

var elementToAnimate= document.querySelector("[data-acc-text='ghost']");



var player = GetPlayer(); 

var currentGhostOpacity = player.GetVar("SL_currentGhostOpacity"); 

currentGhostOpacity = currentGhostOpacity - 10; 
currentGhostOpacity = currentGhostOpacity/100; 

if (currentGhostOpacity >= 0)
{
gsap.to(elementToAnimate, {
opacity:currentGhostOpacity,
duration:2
});

currentGhostOpacity = currentGhostOpacity*100;

player.SetVar("SL_currentGhostOpacity",currentGhostOpacity);
};

```

#### 4 - Scale

```js {linenos=true}

var elementToAnimate= document.querySelector("[data-acc-text='lungs']");


gsap.to(elementToAnimate, {
    scale:0.95,
    duration:2,
    yoyo:true,
    repeat:-1,
    ease: "sine.inOut",
    });

```

#### 5 - Rotation

```js {linenos=true}
var star3 = document.querySelectorAll("[data-acc-text='star-3']");


gsap.to(star3, 12, {rotation:360, ease:Linear.easeNone, repeat:-1, transformOrigin: "50% -50%"});

```

#### 6 - Slider

```js {linenos=true}

var animationTarget = document.querySelector("[data-acc-text='star']");

var sliderStart = 230;
var sliderEnd = 720;
var sliderLength = sliderEnd - sliderStart;

var player = GetPlayer();
var sliderPosition = player.GetVar("sliderPosition");

var sliderRotation = (sliderPosition - sliderStart) / sliderLength * 360;

var sliderOpacity = 1- ((sliderPosition - sliderStart) / sliderLength);

gsap.set(animationTarget, {
    x:sliderPosition,
    rotation:sliderRotation,
    opacity:sliderOpacity
});


```

#### 7 - Stagger

```js {linenos=true}

var animationTarget = document.querySelectorAll("[data-acc-text='vehicle']");

gsap.to(animationTarget, {
    x: "+=50",
    stagger: 1, 
  });

```

#### 8 - Timelines

```js {linenos=true}
var car = document.querySelector("[data-acc-text='car']");
var van = document.querySelector("[data-acc-text='van']");
var motorbike = document.querySelector("[data-acc-text='motorbike']");

let myTimeline = gsap.timeline();

myTimeline.to(motorbike, {x:"+=100", duration: 3});
myTimeline.to(van, {x:"+=70", duration: 1}, "<");
myTimeline.to(car, {x:"+=50", ease:"back.inOut" , duration: 2}, "+=1");

```


#### 9 - Animated counter

```js {linenos=true}

var animationTarget = document.querySelector("[data-acc-text='counter']");

gsap.from(animationTarget, { 
    y:"-1100",
    duration:3,
    ease:"power1.inOut",
  });

```

#### 10 - Heart timeline

```js {linenos=true}
var heart = document.querySelector("[data-acc-text='heart']");

let timeline = gsap.timeline();

timeline.to(heart, {scale: 1.05, ease:"power1.in", duration:0.2});
timeline.to(heart, {scale: 0.95, ease:"power1.in", duration:1});
timeline.repeat(-1);
timeline.yoyo(true);

```

```js {linenos=true}

var heartTimeline = document.querySelector("[data-acc-text='heartTimeline']");

var player = GetPlayer();
var sliderPosition = player.GetVar("heartTimelineSliderPosition");

var invertedSliderPosition = 1 - sliderPosition

gsap.set(heartTimeline, {
    x:invertedSliderPosition,
});

```

#### 11 - Card flip


```js {linenos=true}
var card_front = document.querySelector("[data-acc-text='card_front']");
var card_back = document.querySelector("[data-acc-text='card_back']");

let card_back_timeline = gsap.timeline();

card_back_timeline.set(card_front,{rotateY:90});
card_back_timeline.to(card_back,{rotateY:90, duration:0.5});
card_back_timeline.to(card_front,{rotateY:0, duration:0.5});

```

```js {linenos=true}
var card_front = document.querySelector("[data-acc-text='card_front']");
var card_back = document.querySelector("[data-acc-text='card_back']");

let card_front_timeline = gsap.timeline();

card_front_timeline.set(card_back,{rotateY:-90});
card_front_timeline.to(card_front,{rotateY:-90, duration:0.5});
card_front_timeline.to(card_back,{rotateY:0, duration:0.5});

```

#### 12 - Animated countdown

```js {linenos=true}
var player = GetPlayer();
var myNumber = player.GetVar("myNumber");

gsap.to(
    {value:myNumber},
    {duration:10, value:1500, ease:"linear", onUpdate:function(){
        myNumber = Math.round(this.targets()[0].value / 50) * 50;
        console.log(myNumber);
        player.SetVar("myNumber",myNumber);
    },
    onComplete:function(){
        console.log("animation complete!");
    }

}
);

```

#### 13 - Image carousel

```js {linenos=true}
var animationTarget = document.querySelector("[data-acc-text='group_1']");

//if button_back is pressed
gsap.to(animationTarget, {
    duration:2,
    x:"-=15vw"
});

```

```js {linenos=true}
var animationTarget = document.querySelector("[data-acc-text='group_1']");

//if button_forward is pressed
gsap.to(animationTarget, {
    duration:2,
    x:"+=15vw"
});

```

#### 14 - Wheel of fortune


```js {linenos=true}
var animationTarget = document.querySelector("[data-acc-text='wheelOfFortune']");

var player = GetPlayer();
var SL_rotation = player.GetVar("wheelOfFortuneRotation");

var maximumRotation = 720;

function getRandomInt(max) {
    return Math.floor(Math.random() * max);
  }


var randomRotation = getRandomInt(maximumRotation);

player.SetVar("wheelOfFortuneRotation", randomRotation);


gsap.to(animationTarget, {
    rotation: "+=" + randomRotation,
    duration:3
});

```

#### 15 - Boom boom device

```js {linenos=true}
// on timeline start

var boomMessage = document.querySelectorAll("[data-acc-text='boomMessage']");
gsap.set(boomMessage, {opacity:0});

```

```js {linenos=true}
// when button is clicked

var player = GetPlayer();
var myNumber = player.GetVar("boomBoomTimer");

var windowPanes = document.querySelectorAll("[data-acc-text='window']");
var boomMessage = document.querySelectorAll("[data-acc-text='boomMessage']");
var boomContainer = document.querySelectorAll("[data-acc-text='boomBoomContainer']");

gsap.to(
    {value:myNumber},
    {duration:5, value:0, ease:"linear", onUpdate:function(){
        myNumber = Math.round(this.targets()[0].value);
        player.SetVar("boomBoomTimer",myNumber);
    },
    onComplete:function(){
        console.log("animation complete!");
        gsap.set(boomContainer, {opacity:0});
        gsap.set(boomMessage, {opacity:1});
        gsap.to(windowPanes, {xPercent:-200, yPercent:1000, stagger:0.2});
    }

}
);

```
