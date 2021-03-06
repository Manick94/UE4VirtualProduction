# VPStudio, my Virtual Production tutorials for Unreal 4.26

VPStudio is my latest set of tutorials, all the features of my older work are in here now so please use this one. Feel free to use anything here in your own projects, if you can please credit me, Greg Corson, for helping you out.  This release REQUIRES Unreal 4.26.

Subscribe to [my youtube channel](https://www.youtube.com/user/GregCorson) for updates, tutorials and demos of virtual production. You can also ask for help on [this discord channel](https://discord.gg/ReEhkhc)or this [facebook group](https://www.facebook.com/groups/virtualproduction)

# PLEASE BE SURE TO BACKUP YOUR OLD PROJECTS!!

The Unreal Engine changes to use LiveLink seem to be a major improvement but it is still VERY NEW so please keep copies of your old projects to fall back on if you don't like the way it works.

# What's new in Release 8 (NOT COMPLETE) [older releases here](https://github.com/MiloMindbender/UE4VirtualProduction/releases)

* The old LiveLinkTelemetrySender and MotionControllerTelemetrySender and their demo maps have been replaced with "ActorTransformTelemetry" which works with any type of actor.

# Updating to New Releases

BACKUP your old VPStudio and other projects before trying to update them!

All my releases are numbered with integers starting at 1, the largest release number will be the latest one.  Changes may be large or small, check the release notes for details.

The main branch of github is updated FREQUENTLY, cloning or downloading a ZIP from the main github page may get you unfinished and untested code.  Please use the [latest release from the releases section](https://github.com/MiloMindbender/UE4VirtualProduction/releaseshere) or clone the repository from the latest release tag.

VPStudio is NOT A FINISHED PRODUCT, it is an example that has to be customized for your hardware and uses.  Keep track of the changes you had to make to previous versions.  Usually these are small and can be quickly copied over to the new VPStudio.

I recommend you start with a clean copy of VPStudio, get it running on your hardware and save it.  Don't add or change anything but what you need to do to get it running.  Save this and don't change it.  To use it with your own content, make a copy of your working VPStudio and copy your own content to it. 

# The sample level IS boaring!

A lot of content, even "free" stuff, is licensed so you can use it in your own games and videos but you CAN NOT redistribute it to other people.  So I can't give you all the content used in my demos.  My samples uses just content built into Unreal.  See the [use your own sets tutorial](https://youtu.be/trlpmm5gI6U) on my YouTube channel for help on using your own content.  Almost all the demos on my channel were done with Epic free content that you can download yourself and use with VPStudio.  Epic releases new free content every month.

If you are an artist and would like to help by contributing a better sample level under creative commons license, please let me know.

# Setup VPStudio

Right now VPStudio is setup for an AJA Kona HDMI video capture card and VIVE trackers.  If you have a BlackMagic DeckLink or other card/webcam you will need to replace the assets found in the Aja folder with ones for your hardware.  Look at [Unreal Pro Video](https://docs.unrealengine.com/en-US/Engine/ProVideoIO/index.html) for how to set up different BlackMagic and Aja cards. [Using WebCams](https://docs.unrealengine.com/en-US/Engine/MediaFramework/HowTo/UsingWebCams/index.html) shows how to use most USB webcams.  If you are not using VIVE hardware, you will have to make your own tracker actors.  See VPStudioCore->Trackers folder for examples.

Follow [tutorial 1](https://youtu.be/wWPZjX29asM) and [tutorial 2](https://youtu.be/kRUbUaESw80) to make a rig in Unreal that shows how your camera and tracker are mounted.  There are sample rigs in VPStudio but if they don't match your camera/lens/tracker setup you won't get good alignment of real and virtual objects in your scene.  [Tutorial 3](https://youtu.be/4LjvekNocD4) shows how to setup VIVE controller buttons to control things.  Make sure your VIVE trackers are setup to Special_1, 2, etc. as shown here. [Tutorial 4](https://youtu.be/UGHjwZ6J13E) shows how to setup the studio and fine tune your camera and tracker alignment [totorial 5](https://youtu.be/trlpmm5gI6U) shows how to add your own sets and assets to a copy of VPStudio.
 
# Using your own levels

[Tutorial 5](https://youtu.be/trlpmm5gI6U) shows how to add your own sets and assets to a copy of VPStudio.
 
You make a copy of a working VPStudio project and then "migrate" your level into it.  Once you have your level migrated, you use the "levels" window in the editor to add VPStudioCore as a sublevel and you are ready to go, see the tutorial for more details.

Some levels may do things with lighting that make them appear too bright or too dark.  For now you're on your own about fixing this, I don't have any good advice (yet).

# Known Problems

Under Edit->Project Settings->Project->Maps & Modes I provide a VPPlayerController that manages all user input and controls everything.  This is required or nothing will work.  If you want to use this project with a level that requires it's own PlayerController you will need to figure out how to combine mine and yours. I also provide a VPGameState and VPGameMode which are currently EMPTY and not required.  Though in the future this may change.  

Every time you recompile a VPCamera asset, Unreal disconnects the cameras from the composure passes.  If you recompile these you will have to go back into VPStudioBackground 1 & 2 and the GarbageMatte 1 & 2  and set the "camera source" to override and the Target Camera Actor to VPCamera 1 & 2.

My dual camera system is always rendering both camera views.  If you are having trouble hitting the frame rate you want, go into Window->Composure Compositing and turn off any composure passes you aren't using.  If you only have one camera turn off everything numbered "2".  Depending on what you are filming, you may not need to render all the foreground, background and garbage matte passes either.

# Features

* Commands go through Edit->Project Settings->Engine->Input so they can be changed. You can change the keyboard keys assigned to functions and the speed of movement on this page.  A function can be mapped to almost any input device you have including PC game controllers, joysticks and VR controllers.

* Multiple cameras and video sources are supported.  This lets you have more than one camera view of your talent and live switch between them.  The project is setup for 2 cameras, adding more requires some blueprint and composure changes but I am working to make this simpler.

* When using LiveLink tracking systems, all the cameras and mattes are tracked live in the editor so you can always see the state of your studio.

* You can place several "Talent Markers" where you want your talent to appear in the set.  Pressing a key will teleport your talent between these marks.

* Tracking is all inside "Tracker" actors to make it easier to use different kinds of tracking devices.  This allows easy customization for VIVE, OpenXR, LiveLink and other tracking solutions.  Only the Tracker actor needs to change.

* You can move the talent markers around using keyboard key to get the right placement of them in your level.  This can be done live while the composite is running and you will see the talent moving through the level.

* There are a number of measuring and setup guides to help you measure your real world studio and align it with your virtual set.  This includes a plumbline that always points straight down, "axis guide world" which is always lined up with the world and some tools to automatically measure your camera rig.  TalentMarkMan is 193cm tall or about 6'3", you can rescale it to match the size of your talent.

* The "rig" your camera and trackers are mounted to can be modeled in the system to exactly match your real-world rig.  This includes things like multiple joints that could be moved by a tracker or might need to be "tweaked" if the rig is slightly out of alignment.  A few samples of different rigs are provided.

* There is a garbage matte setup for use with a greenscreen that covers a wall and floor.  If your greenscreen has a different shape, you can model it and add your own mesh for a better fit.  There is a tutorial on my youtube channel that shows how to adjust the garbage matte to match the size of your greenscreen.

* A HUD with guides useful for aligning cameras if your camera doesn't have guides or has no screen.

* You can turn tracking of stationary objects on and off to avoid seeing the jitter that some trackers have when sitting still.


# Keyboard Keys

For the keyboard/mouse/vive tracker commands to work you need to have clicked in the player viewport or PIE window.  To get control back just hit shift-F1 or ESC to quit.

These are what the keyboard keys currently do, if you want to change them go to Edit->Project Settings->Engine->Input.

Right now switching between "Virtual Production Filming" mode and  inspecting the set has to be done by going to the "VPStudio Comp" actor and setting the output pass to "Player Viewport" for filming or "none" for inspecting.  

When you first press PLAY you will either be looking at the composure composite or in inspection mode.  All the movement keys will be setup to move the inspection camera so you don't accidentally move anything else while you are filming.

Depending on what mode you are in, you can move talent markers or the inspection camera around.  Use the standard Unreal W, S, D, A keys for forward, back right and left movemtnt.  E and C moves up and down.  Use the mouse to look around (pan tilt).

To change to Virtual Production camera one, press 1 or left-click the right hand vive controller trackpad.  For camera two, use 2 or click right on the trackpad.

The N key or Vive controller trigger teleports you to the next TalentMark.  You can have as many of these as you want, just drag them into the level and number them 1, 2, 3 and so on.  When you press this key all your tracked objects & cameras will jump to the next mark and your talent will appear in that spot.

The M key switches between VPCamera "raw" views.  This gives you a view from each of your cameras but without any live composite, you will only see the CG part.  (only works when VPStudioComp output is set to NONE)

The I key switches to the inspection camera.  This is just a free floating camera that lets you look around the level while all the cameras and tracked objects are running so you can see if they are working and in the right places. (only works when VPStudioComp output is set to NONE)

The T key toggles between moving the inspection camera and moving the talent marks.

y, u, p, o and k keys will toggle visibility of TalentMark, MeasuringGuide, CameraModel, CameraRig and Tracker actors

When VPStudioComp output is set to "player viewport" you will see the full composite output of live cameras and the CG background.  The 1 and 2 keys switch between VPCamera1 and VPCamera2

Press b or click the right VIVE controller trackpad down to take a screenshot.  This is the same as typing "shot" into the editor command window.

The H key brings up the hud with camera alignment guides.

The L key locks down all the trackers you have set to be "lockable"

# Bugs and Suggestions

I welcome suggestions on how to make this simpler or more efficient.  You can use the github issues tracker or post to my YouTube channel if you find bugs or have feature requests.

