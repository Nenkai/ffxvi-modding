# Intro to Timelines

## What are character timelines

Character timelines represent the sequence of events happening each frame during an action.

Think of them like the timelines in your favorite video editing software:

* The video running in the background corresponds to your character animation

* PNGs and additional videos are your VFX, facial animations

* Sound tracks are your SFX

* Additional properties (such as color correction, parameters) are other stuff, like enabling Stomp execution during a move or configuring animation canceling

Basically, each and every type of event that can run during a timeline's sequence is a different kind of timeline element, each coming with their own parameters.

Common parameters for every timeline element include starting frame and frame duration, which determine when exactly should an element execute and for how long.

Each character timeline is stored inside different .tlb (TimelineBinary) files, located in each character's `timeline/` folder. To find Clive's timelines, for example, you would look inside `data/chara/c1001/timeline/`.

## Other timeline applications

Besides character timelines, which are stored in dedicated .tlb files, there's other types of timelines, found inside other file types:

* Cutscene Timelines - found inside .csb (CutsceneBinary) files

* UI Timelines - found inside .uib (UIBinary) files

* VFX Timelines

* Stageset Timelines 
