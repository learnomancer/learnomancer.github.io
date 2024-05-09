---
title: 'Pick a Random Sentence from a list in Articulate Storyline 360 with JavaScript'
date: 2024-04-28
draft: false
---

In this video tutorial, I'll walk you through the process of creating a dynamic slide in Articulate Storyline 360 where a random sentence from a list appears each time you click a button.

With just a few lines of JavaScript, you can add an interactive element to your e-learning courses that keeps learners engaged and curious.

Here's what we'll cover:

- Setting up the slide and button in Storyline
- Creating a Storyline variable to store the extracted sentence
- Preparing the text box to display sentences of varying lengths
- Adding JavaScript to select a random sentence from a list
- Inserting the extracted sentence back into the Storyline variable
-Testing and publishing the slide to see the random sentence generator in action

## Here's the video
{{< youtube 8pG9kncjcPY >}}

## Code used

```js {linenos=true}

var player = GetPlayer();
var sentence = player.GetVar("sentence");

const missions = [
    "Infiltrate a high-security gala in Monaco to retrieve stolen nuclear codes from a rogue agent.",
    "Disarm a series of strategically placed bombs in a bustling metropolis, racing against a ticking clock.",
    "Pose as a corrupt businessman to gain access to a secret meeting of international arms dealers.",
    "Dive into the depths of the Arctic Ocean to recover a mysterious device from a sunken submarine.",
    "Scale the Burj Khalifa using advanced technology to intercept a crucial data transfer.",
    "Navigate the alleyways of Marrakesh to track down and extract a double agent before they are eliminated.",
    "Attend a high-stakes poker game in Montenegro to uncover a financier funding global terrorism.",
    "Hack into a secure server in Shanghai to erase all traces of a false identity created by enemy spies.",
    "Survive a relentless pursuit through the jungles of South America after obtaining vital intelligence.",
    "Disguise and insert into a paramilitary group in Eastern Europe to prevent a violent uprising.",
    "Sneak onto a luxury yacht in the Mediterranean Sea to capture a key suspect without alerting the security detail.",
    "Decode an encrypted message that points to a hidden cache of chemical weapons in a remote Siberian facility.",
    "Disguise as a renowned art dealer to attend an exclusive auction where a stolen microchip is being sold.",
    "Pilot a stealth drone over hostile territory to gather critical intelligence on a new missile system.",
    "Negotiate the release of hostages from a fortified compound in North Africa under the guise of a diplomat.",
    "Track down a cyber-terrorist in Tokyo using only bits of information from intercepted communications.",
    "Plant surveillance devices in the embassy of a hostile nation during a high-profile diplomatic reception.",
    "Retrieve a rare piece of technology from a heavily guarded research lab in Silicon Valley.",
    "Infiltrate a rogue faction's training camp to thwart a planned attack on an international summit.",
    "Escape from a high-speed train carrying a defector who possesses knowledge about a corrupt government official."
];

sentence = missions[Math.floor(Math.random() * missions.length)];

player.SetVar("sentence", sentence);

```