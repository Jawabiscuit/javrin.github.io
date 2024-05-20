---
title: UE5 Game Dev Log
date: 2024-04-18T19:41:31-04:00
categories:
  - Dev
draft: false
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
tags:
  - ue5
created: 2024-04-18 19:41
modification date: 2024-04-18 19:41
---
Today's development sessions were about creating a dash roll mechanic for the character and re-animating bits of her locomotion animation in Cascadeur after the retargeting from UE5 mannequin. The video is mostly me noodling around in Cascadeur which I've been evaluating for character animation then applying the cleaned animation into the game and finally testing it along with the other fun new features I added.

&nbsp;

{{< youtube SNfOGZcqMhY >}}

## About the Character

The character model and rig I'm working with is from the Shadow Fight Arena 4 game, which I have zero experience with playing, provided by the talented team at Cascadeur on Renderhub. I chose her for the accessories she has to animate. It's a decent character, but the rig definitely isn't the cleanest. She's functional but not reusable so the goal is to eventually rebuild her into a more polished portfolio piece. This process is testing my knowledge of many aspects of character development and if it's possible I'd also like to share the final rig.

The rig was prepared in Maya for Chaos cloth and physics simulations, ensuring that it can achieve realistic cloth dynamics within UE5. For this character, I've simulated the chest, earrings, and the back of the bandana, adding an extra layer of realism and movement to the overall look.

## Today's Accomplishments

**Dash Collision Actor and Movement Mechanic**

Taking inspiration from the iconic Sonic the Hedgehog games, I implemented a "Dash" collision actor and character movement mechanic. The player is able to perform a dash roll using the controller or get launched by overlapping with the actor placed in the world.

This is achieved using some vector multiplication combined with "Launch Character" function and a rolling animation montage, and allows our character to perform a lightning-fast dash or roll, adding an exciting yet over-powered dodge/movement ability to the gameplay. It will need to be fine-tuned but it's fun for the time being.

**Animation Retargeting and Refinement**

I successfully retargeted the UE Mannequin animations over to the custom character rig, but the retargeted animations are, as usual, only a good starting point for gross character movements as they aren't very appealing. So I took the time to start reanimating the locomotion beginning with idle and walk-in-place animations. Next, I will tackle the walk and run motions.

Cascadeur is making quick work out of this process. I had only intended to clean up the retargeted motion however I ended up throwing most of the original animation out and taking a few key poses and sprucing them up here and there. Even so, with the help of Cascadeur's smart autoposing rig and unbake animation tool, I was able to make quick work of it. 

Overall, it was a productive day filled with promising advancements in character animation and movement mechanics. Stay tuned for more updates as I continue to tweak and add more to this character in Unreal Engine 5.