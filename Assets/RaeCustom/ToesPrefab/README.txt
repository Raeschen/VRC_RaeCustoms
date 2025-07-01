This is a lil prefab to allow you to curl/spread your paws depending on the angle of your ankle!

Curl ankle down, the paws close up. curl ankle up, the paw digits spread. Side to side is also possible and included

PREREQUISITES:
VRCfury

Features:
"2ax" : 2-axis. Up/down per left and right foot. Uses 2 floats total (one per axis)
"4ax" : 4-axis. Up/down/left/right per left and right foot. Uses 4 floats total (one per axis)
Main toggle to disable functionality entirely.


Included are:
-Premade version for Nardobat(and nardoragon probably) in 2ax (4ax animations exist)
-Premade version for Antigen in 2ax(4ax animations exist)
-Blank version for both 2ax and 4ax for customising to any other avatar!

To use a premade version (Nardo, antigen), simply click and drag the prefab onto the avatar root. Done!

To use the blank versions for any other avatar, simply do the following:
-Duplicate "FX ToesController Blank 2/4ax" and prefab "Toes Controller Blank 2/4ax"
-Rename the prefab and FX controller to whatever you want (e.g. FX ToesController myavatar, Toes Controller myavatar)
-Click the new prefab. Replace "FX ToesController Blank 2/4ax" in the VRCfury Full Controller component with your duplicated, renamed FX controller. LEAVE the contact driver FX and the contact driver params alone.
-In the animations folder, duplicate the 'Blank' folder. rename the duplicated folder to whatever you want (e.g. myavatar)
-Open your new FX animation controller. In the single layer, doubleclick the blend tree. In blendtrees "Left" and "Right", replace all the animations with ones from your newly duplicated folder.
-Duplicate your model. In the animator on the model's root layer, assign your new FX controller. Use this duplicate to create animations for curling, spreading, and twisting your toes into each appropriate animation. Delete the duplicate when finished.
-With your custom avatar's FX layer set up and assigned in your custom prefab, click and drag the prefab onto your avatar's ROOT
-Underneath the Toes Controller prefab are two objects "Left" and "Right". Align these to the roots of your ankle bones (You can use a position constraint. Add position constraint. Constrain "Left" to your left ankle/foot bone, click 'zero', then delete the position constraint. Repeat for right.)


Potential issues:
Does your avatar have a paw puppet control? Make sure the prefab is BELOW it on the heirachy to allow this to supercede
Does your avatar have physbones on the paws? Make sure "Is Animated" is checked or this won't work!
Something else? Ask! <3