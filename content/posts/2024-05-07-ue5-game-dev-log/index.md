---
title: UE5 Game Dev Log
date: 2024-05-07T16:03:39-04:00
categories:
  - Dev
draft: false
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
  - name: image-01
    src: UnrealEditor_FastFlight_Deactivate_Event.png
  - name: image-02
    src: UnrealEditor_FastFlight_Deactivate_Function.png
  - name: image-03
    src: UnrealEditor_Live_Retarget_AnimBP.png
  - name: image-04
    src: UnrealEditor_Live_Retarget_CharacterBP.png
  - name: image-05
    src: UnrealEditor_Live_Retarget_AnimGraph.png
  - name: image-06
    src: UnrealEditor_Live_Retarget_AnimGraph_2.png
  - name: image-07
    src: UnrealEditor_Switch_Mesh_Visibility.png
  - name: image-08
    src: UnrealEditor_Switch_Mesh_Opacity_BeginPlay.png
  - name: image-09
    src: UnrealEditor_Switch_Mesh_Opacity.png
tags:
  - ue5
created: 2024-05-07 16:03
modification date: 2024-05-07 16:03
---
# Superhero Flight, Diving, and Mesh Swapping

In the past week I've been soaring to new frontiers with some insanely cool new mechanics like diving, superhero hero flight and a simple but powerful technique for swapping character meshes at runtime that I never knew about!

&nbsp;

{{< youtube ANU1FHvSTXo >}}

## Superhero Flight Mechanics

Yep, if you've been paying attention, superhero flight gameplay has been trending lately and while I'm not making a game in the Marvel universe any time soon, it's actually quite fun and relaxing to play with and it would definitely come in handy as a, somewhat OP, "god mode" for any game. The implementation uses a mix of vector math for responsive control over aerial movements and blended animations and additives for body animation and transitions.

You can hover around or kick it into high gear in fast flight mode that'll make you feel like you're going 0 to plaid in a Tesla, well maybe not quite 😉. By the way, there has been a system available like this in the Marketplace but this one is made from scratch, except for the animations which I'll no doubt end up modifying too. To amplify the intensity, I've cooked up some simple but effective visual effects. Camera shakes, FOV adjustments, and animated shockwave (stand-in geometry for now) are being used to sell that blistering velocity.

## Dive Gameplay

I hear you saying "Meh", and I'd heartily agree 😆, but let me introduce the diving mechanic that's sure to give you that freefall rush. You can leap from towering heights and plummet towards the ground with reckless abandon making you feel like a base jumping daredevil. This feature also has two states, falling and diving. Falling happens automatically when the character's movement status is "falling", just after jumping for instance. When falling, the character takes a semi-prone pose similar to skydivers when they are in a controlled decent. The dive input will transition the character into an active head-first plunge and increase the acceleration towards the ground.

## Mesh Swap and Live Retargeting

For something completely different but equally awesome, I recently figured out how to swap in and out a character's mesh and run retargeting live at runtime. So you can swap between entirely different character meshes on-the-fly, but the kicker is the retargeted character will animate flawlessly, mirroring the source character's movements exactly in real time. Mind = blown? And, this is all very easily achieved inside Unreal with its retargeting system and the use of a single Blueprint node in the animation graph!

## Under the Hood

Now that I've hyped the new animation capabilities, let's dive into some interesting aspects of how these mechanics were created. Keep in mind, this isn't a step-by-step how-to although I would be delighted to break each of these mechanics down into separate videos or posts. Lemme know if that interests you! What follows is more of a breakdown of each mechanic and specific challenges I faced with implementing each.

### Flying

- Uses the Enhanced Input Action system to map either keyboard or gamepad input to actions
- Uses vector math to control direction, rotation, velocity
- Blended animations for body movement 
- Two modes: normal hover flight and fast flight
- Visual effects like camera FOV interpolation, shakes, stand-in shock wave geometry

&nbsp;

Fast flight was pretty straight-forward to implement, but deactivating fast flight, since it is a key press, presented a bit of a challenge. It was very easy to get into a state where the VFX would trigger unintentionally or the fast flight wouldn't deactivate correctly if the button was held down but a direction input wasn't coming from the controller.

I recognized this as a pattern that I've solved before using timers so I decided to go that route, but only after failing to get the result I was after by switching from two individual pressed and released triggers to a single hold and release trigger. This solution works by firing an event intermittently using timers after the input action event enters the triggered state. Fast flight should be disabled only if the condition to deactivate is true. The condition logic is bundled up into a function for legibility, but fast flight should be disabled when the character is moving very slowly.

&nbsp;

{{< image src="UnrealEditor_FastFlight_Deactivate_Event.png" caption="DeactivateFastFlight Event" src_l="UnrealEditor_FastFlight_Deactivate_Event.png" >}}

{{< image src="UnrealEditor_FastFlight_Deactivate_Function.png" caption="FastFlightShouldDeactivate Function" src_l="UnrealEditor_FastFlight_Deactivate_Function.png" >}}

### Diving

- Allows base jumping off ledges or freefall in mid-air by deactivating flight
- Two states: falling (semi-prone) and diving (head-first)
- Camera FOV and effects enhance experience

&nbsp;

I hit a snag while animating the blend transitions for this mechanic. I decided I'd try animating in Unreal using only the Mannequin control rig, which worked fine, but when I tried using the exported animation the character would not orient itself face down while diving. It seemed as if the motion did not get baked down from controls to bones correctly. My quick solution was to use animation that was exported from a Maya but I intend on finding a solution without having to do that.  

### Mesh Swap

This technique is a game-changer, giving animators and developers the freedom to test animations across multiple rigs without missing a beat making it a proxy rig of sorts. It could also be used to swap character models mid-game for a unique twist!

Implementing was as really simple. That's partially because I had already set up a retargeter rig for my character and the Unreal Mannequins (before the 5.4 retargeter system updates). All that was left was I had to create a new Animation BP for my character and connected up a "Retarget Pose from Mesh" node to the Output Pose in the Anim Graph. Lastly, I needed to assign a target Skeletal Mesh as a secondary mesh in the character blueprint. I gave it the name "Other Mesh" as it could potentially be swapped out for any number of meshes.

&nbsp;

{{< image src="UnrealEditor_Live_Retarget_AnimBP.png" caption="Creating a new Anim BP" src_l="UnrealEditor_Live_Retarget_AnimBP.png" >}}

{{< image src="UnrealEditor_Live_Retarget_CharacterBP.png" caption="Secondary mesh parented to the character's primary mesh" src_l="UnrealEditor_Live_Retarget_CharacterBP.png" >}}

{{< image src="UnrealEditor_Live_Retarget_AnimGraph.png" caption="Retarget Pose from Mesh node" src_l="UnrealEditor_Live_Retarget_AnimGraph.png" >}}

{{< image src="UnrealEditor_Live_Retarget_AnimGraph_2.png" caption="Assign a retargeter rig" src_l="UnrealEditor_Live_Retarget_AnimGraph_2.png" >}}

An unexpected issue that I had to solve with this technique is that toggling the mesh's visibility would break the retargeting. Doing so made the character movement quite peculiar! It was as though the capsule would move around but the character's body would remain rigid.

&nbsp;

{{< image src="UnrealEditor_Switch_Mesh_Visibility.png" caption="Solution 1: Mesh visibility key press event" src_l="UnrealEditor_Switch_Mesh_Visibility.png" >}}

My solution? Apply a transparent material instance to the meshes instead! This way, I could achieve the same visual effect without disrupting the animation flow. It was a bit more complex of a graph but it works and could be improved to accept any number of source and destination materials.

&nbsp;

{{< image src="UnrealEditor_Switch_Mesh_Opacity_BeginPlay.png" caption="Solution 2: Material opacity - Begin Play" src_l="UnrealEditor_Switch_Mesh_Opacity_BeginPlay.png" >}}
{{< image src="UnrealEditor_Switch_Mesh_Opacity.png" caption="Solution 2: Material opacity key press event" src_l="UnrealEditor_Switch_Mesh_Opacity.png" >}}

## Future Polish and Frontiers

We're just getting started with these mechanics. There's still plenty of room to push them even further and unlock new frontiers in character animation and gameplay.

With flight, I've got some slick ideas for added polish and depth. Implementing a satisfying landing animation could go a long way in selling the impact and help with immersion. Or how about special transition animations that let you seamlessly dive from flight into a stunt plane-like nose dive? The potential for crazy aerial maneuvers is through the roof.

The dive mechanic is also ripe for enhancements. Unique landing reactions based on surface type or adding the ability to transition into a roll could make for some insanely cool stunt sequences. The gameplay animation combos are endless!
The freefall mode of diving could also be enhanced by giving the player more control over lateral movement for an experience that more closely mimics real life skydiving.

As for the mesh swap system, I'm just scratching the surface there too. Combining this technique with procedural animation setup could allow for some wild shape-shifting abilities. Or what if we could blend between multiple character rigs simultaneously? Talk about an animator's playground!

Of course, no new feature is complete without dreaming up fresh ideas for visual effects. I'm already tinkering with concepts like contrail effects during high-speed flight, objects that react physically to displacement forces of the character's movement, and even environmental impacts like billowing smoke or cracking pavement on those high-impact landings.

The road ahead is filled with exciting opportunities to keep pushing the boundaries of what's possible in VFX, animation and gameplay. I can't wait to get my hands dirty and see where this creative journey takes us next.

So hang tight, folks! This is just the beginning. With each passing day, I'll be refining these mechanics, implementing new enhancements, and dreaming up even crazier stunts for you to experience. The animation frontier remains wide open, and I'll be sure to share all the thrilling developments right here in future installments.

Stay animated, my friends!