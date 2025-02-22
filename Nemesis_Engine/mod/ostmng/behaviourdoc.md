# Quickstart Docs
## Graph Events
Register for graph events with [`RegisterForAnimationEvent`](https://www.creationkit.com/index.php?title=RegisterForAnimationEvent_-_Form) in Papyrus, send them to the graph with [`SendAnimationEvent`](https://www.creationkit.com/index.php?title=SendAnimationEvent_-_Debug). Events are actor-specific and independant.

Events sent from the IAnimationGraphHolder to the behaviour graph will not be caught by other code, and vice versa. **Events can only be received via papyrus if they are sent from the graph itself.**

To send events through animation graphs with precise timestamps, use [hkanno64](https://www.nexusmods.com/skyrimspecialedition/mods/54244) to unpack the animation hkx and add annos via text file, then build. [Video tutorial for hkanno here](https://www.youtube.com/watch?v=VFwW9dVUZiE)

Annotation = Graph Event, but annotation is used to refer to events that are embedded inside animation files specifically.
### Graph Triggers
`OST_EnterSceneReady` - Go into scene ready state; blocks transitions, disables stagger and headtracking. 

`OST_ExitSceneReady` - Exit scene ready state. Must be called on exiting scene.

`OST_DisableFootIK` - Disable FootIK (correction of character lower body to account for slopes/slants). Experimental.

`OST_EnableFootIK` - Enable FootIK

`OST_StartAnimatedCamera` - Starts animated camera, control it with Camera3rd bone in animations.

`OST_EndAnimatedCamera` - Ends animated camera.

### Transition Blocking
The `SceneReady` events block certain input transitions like drawing/sheathing weapons until after they exit scene ready.

### Dummy Events
Dummy events do nothing on the graph end, they are intended to be used as a piggyback for animations to communicate via annos with listening code, which can then carry out the appropriate actions

`OST_ThrustIn`

`OST_ThrustOut`

`OST_UndressActor`


## Graph Variables
Use [SetAnimationVariable<Type>](https://www.creationkit.com/index.php?title=SetAnimationVariableInt_-_ObjectReference) to set variables, and [GetAnimationVariable<Type>](https://www.creationkit.com/index.php?title=GetAnimationVariableInt_-_ObjectReference) to get them. The first five variables need to be binded to the anim clips they want to control via behaviour, this can be done with the Animlist Transition Tool.
  
All variables are actor specific, persistent and only reset alongside the graph reset(usually race/sex change). 
  
'OST_Installed' (bool) returns true if behaviour patch installed, else none. 
  
`OST_InScene` (bool) don't change this manually unless you want to block transitions only, usually you want OST_EnterSceneReady.
  
`<modprefix>_AnimationSpeed` (float)
  
`<modprefix>_CropAnimStart` (float)
  
`<modprefix>_CropAnimEnd` (float)
  
`<modprefix>_AnimStartTime` (float)
  
`<modprefix>_TransitionDuration` (float)
  
`<modprefix>_UndressTargetSlot` (float)
  

