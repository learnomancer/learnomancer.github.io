---
title: 'Create a Gamified Progress Bar in Articulate Storyline 360 using Javascript'
date: 2024-04-21
draft: false
---

In this video, we'll go through a bit of a tutorial on how to explore the practical side of gamification by crafting a dynamic progress bar in Articulate Storyline 360 that updates when the user earns points or gains levels.

The scenario: The user gains some experience points when they're correctly answering a question. When they reach 1000 XP points, they gain a level. I want to show their progress using a progress bar.

🎮 What I'm attempting here is to replicate the progress bars commonly seen in video games, trying to make learning feel more like a rewarding journey and impart a sense of achievement.

I also reference Duolingo, the language learning app, because I think they've implemented a cool progress bar which actually helps learners measure their learning objectives.


💡 Here's what we'll cover :

- Practical tips for setting up your Articulate Storyline project efficiently.
- A breakdown of the JavaScript code required to create an interactive progress bar.
- Solutions to common challenges you might face while implementing this functionality in your projects.

## Here's the video
{{< youtube oSG09lrcSW8 >}}

## Code used

```js {linenos=true}
var progressBar = document.querySelector("[data-acc-text='progressBar']");
var levelText = document.querySelector("[data-acc-text='levelText']");
var player = GetPlayer();
var XP_requiredPoints = player.GetVar("XP_requiredPoints");
var XP_displayedPoints = player.GetVar("XP_displayedPoints");
var XP_gainedPoints = player.GetVar("XP_gainedPoints");
var XP_totalUserPoints = player.GetVar("XP_totalUserPoints")
var objectScale;
var currentLevel = player.GetVar("currentLevel");;
var levelsGained;

XP_displayedPoints = XP_displayedPoints + XP_gainedPoints;
XP_totalUserPoints = XP_totalUserPoints + XP_gainedPoints;
player.SetVar("XP_totalUserPoints",XP_totalUserPoints);

//add level
levelsGained = Math.floor(XP_displayedPoints / XP_requiredPoints);
currentLevel = currentLevel + levelsGained;
player.SetVar("currentLevel", currentLevel);

if(levelsGained >= 1){
    gsap.to(levelText, {scale:1.2, repeat:1, yoyo:true, ease: "power2.inOut"});
};


if (XP_displayedPoints >= XP_requiredPoints)
    {
    XP_displayedPoints = XP_displayedPoints - XP_requiredPoints;

    player.SetVar("XP_displayedPoints",XP_displayedPoints);

    }
else{
    player.SetVar("XP_displayedPoints",XP_displayedPoints);
    };


objectScale = XP_displayedPoints / XP_requiredPoints;


// Animate the progress bar from the current scale to the new scale
gsap.to(progressBar, {
  scaleX: objectScale,
  duration: 1, 
  ease: "power2.inOut",
  transformOrigin: "center left"
});

```