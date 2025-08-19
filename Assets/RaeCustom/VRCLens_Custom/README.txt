VRCLens Streaming/CamOps Addon Pack

PREREQUISITES:
-VRCLens (v1.9.2)
-VRCFury
-Poiyomi's Toon Shader

NOTES:
- This pack consists of three parts;
-- VRCLens "Blue Dragon" Camera model with Tally Light
-- VRCLens "Sync Fix" tweak
-- VRCLens "Smooth zoom" tweak
- Each part is optional and not reliant on other parts.
- "Vector3()" values can be directly copied and pasted into XYZ fields to fill all three values at once.
- Usage of VRCFury "Parameter Compressor" is fine and shouldn't cause issues. Recommended if you're low on synced parameters


QUICK CHECKLIST IF UPDATING/REAPPLYING VRCLENS AFTER ADDING THESE ADDONS:
> Re-set GameObject <avatar>/VRCLens/WorldC/CamPickupAlways/PreviewBase Rotation X to 41 ( Vector3(41,0,0) )
> Make sure all addon prefabs exist
> Re-check Avatar Base FX layer - Remove all layers corresponding to addons (SyncFix:Step 5, SmoothZoom: Step 5)
> Re-check "<avatar>/VRCLens/WorldC/CamPickup/CamBase" Parent Constraint (RootMount and OSCController add sources to this)
> Re-check any tips that need repeating on reapplying VRCLens


INSTALLATION:
====================================================================
======================= BLUE DRAGON CAMERA =========================
====================================================================

INFO:
Top-preview mesh:1458 Tris
Rear-preview mesh:1466 Tris
1 Material
Preconfigured Prefabs for VRCTally + shaders

PRECONFIGURE:
Multiple Mesh options exist for the Blue Dragon Camera:
- Preview-screen mounted rear mesh
- Preview-screen mounted top mesh
Multiple Shader options exist for the Blue Dragon Camera:
- Unity Standard
- Poiyomi, with TallyLight
- Poiyomi, with TallyLight + Audiolink effect + Video Texture effect (DEFAULT)
Feel free to open the prefabs and change which shader is assigned!
Feel free also to edit the VRCTally VRCFURY parts on the root of the camera prefabs (i.e. the menu path, ect)
Do this BEFORE applying the camera as VRCLens UNPACKS the prefabs!

USAGE:
1) Use VRC Lens as normal: Add the VRCLens main prefab to your scene.
2) In the VRC Lens Setup Script;
2.1) Change the Camera Model to Blue Dragon Camera, either RearPreview (Preview screen on rear) or TopPreview(Preview screen on top)
2.2) Click "Change Camera Model"
2.3) Change field "Camera Scale" to 1 (Or whatever you want)
2.4) Change field "Preview Scale" to 0.155
2.5) Change field "Preview Position" to;
2.5.1) If using RearPreview: Vector3(0,0.0357,-0.515)
2.5.2) If using TopPreview: Vector3(0,0.2335,-0.1465)
2.6) The Preview screen will be tilted incorrectly - This is normal! We'll fix this later.
2.7) Position the Hand Camera and Head Camera however you wish. Helpful tip for Head Camera below!
2.7.1) You can place the Camera Prefab under "VRCLens/HeadMountPoint" to sample how the headmount will look, BUT DELETE THE CAMERA PREFAB WHEN DONE!
2.8) Customise the remaining VRCLens settings (See SMOOTH ZOOM step 1 if using, NOW before applying!) and then apply VRCLens
3) After applying VRCLens, look for the VRCLens Prefab under your avatar's root.
3.1) Navigate to <avatar>/VRCLens/WorldC/CamPickupAlways/PreviewBase
3.2) Alter PreviewBase's Rotation to: Vector3(41,0,0)

Tally light toggle is under menu path: VRCLens/Custom/VRCTally
Done! Either upload, or move on to other addons below.


====================================================================
============================ SYNC FIX ==============================
====================================================================

An Alteration to make VRCLens sync to remote players more reliably.

INFO:
- +6 synced parameter bits to facilitate sync
- Fixed sync includes State (On/off/inhand/onhead/dropped/handrotating/lens hidden/lens shown)
- Fixed sync DOES NOT include dropped POSITION or drone-fly POSITION. World-dropped position will desync to remote users that late-load you. This is a VRChat limitation.
- Current version designed for VRCLens v1.9.2

Steps:
1) Use VRCLens as normal, add it to an avatar
2) After adding, add the "RaeCustom_VRCLens_SyncFix" prefab under your avatar root.
3) Go to your Avatar's root. Check the Avatar Descriptor, navigate to the FX layer assigned.
4) Open your base FX layer in the Animator tab.
5) Delete the following animator layer(s);
5.1) vCNT_Base 225/254/255 i5
5.2) vCNT_Drop 250-252 [1B] i1,t23
5.3) vCNT_AttachSwap 223
5.4) vCNT_StealthLens 225

Note: Check "Quick Checklist" at the top of this README if you're re-applying VRCLens! some steps must be repeated.

VRCLens should now sync it's state to remote users better.


====================================================================
========================== SMOOTH ZOOM =============================
====================================================================

An Alteration to make VRCLens's Radial Zoom smoothed using VRCFury's parameter smoothing

INFO:
- 0 Synced bits (Zoom is local only)
- Current version designed for VRCLens v1.9.2

PRECONFIGURE:
- Feel free to open the ""RaeCustom_VRCLens_SmoothZoom" prefab and edit;
-- The menu path for the menu (Default is /VRCLens/Custom) in the VRCfury Full Controller
-- Under the "Advanced Options" tab in the VRCFury Full Controller, you can alter the "Duration(sec)" for smoothed parameter "VRCLZoomRadial". 
--- A greater number is more smoothing.

Steps:
1) On the VRC Lens Setup script, make sure that the "Use Zoom Dial" is UNCHECKED. Import VRCLens.
2) After adding, add the "RaeCustom_VRCLens_SmoothZoom" prefab under your avatar root.
3) Go to your Avatar's root. Check the Avatar Descriptor, navigate to the FX layer assigned.
4) Open your base FX layer in the Animator tab.
5) Delete the following animator layer(s);
5.1) vCNR_Zoom

Note: Check "Quick Checklist" at the top of this README if you're re-applying VRCLens! some steps must be repeated.

Smooth zoom radial is under menu path: VRCLens/Custom
VRCLens should now zoom (Both with zoom buttons and with the zoom radial under VRCLens/Custom) much more smoothly.


====================================================================
========================== ROOT MOUNT ==============================
====================================================================

A fully synced 'mount' that sits infront of you, tracks your avatar root, and can be hand-puppetted. 

INFO:
- Several synced booleans, Parameter-compressable to effectively 0 using VRCFury parameter compressor (Compress bools)
- Current version designed for VRCLens v1.9.2

Steps:
1) Add the "RaeCustom_VRCLens_RootMount" prefab under your avatar root. It MUST BE LOWER Than SyncFix on the hierarchy!
2) Navigate to "<avatar>/VRCLens/WorldC/CamPickup/CamBase"
3.1) On Object CamBase, Locate the Parent constraint.
3.1.1) By default, this parent constraint has THREE Sources.
3.1.2) Add a FOURTH(4th) Source.
3.1.3) Set the FOURTH(4th) source WEIGHT to 0
3.1.4) Set the FOURTH(4th) source to "<avatar>/RaeCustom_VRCLens_RootMount/RootMount/RootMount_Offset/RootMount_PhysRoot/RootMount_CamBase"
4) If you wish to customise the rootmount's mount position, edit the position of "<avatar>/RaeCustom_VRCLens_RootMount/RootMount/RootMount_Offset" to wherever you like.

Done! Access controls in menu path: VRCLens/Custom/RootMount

Note: Check "Quick Checklist" at the top of this README if you're re-applying VRCLens! some steps must be repeated.

====================================================================
========================== OSCControl ==============================
====================================================================

An alternative to drone mode that allows an OSC video game controller (e.g. Xbox controller) to pilot the cam

INFO:
- 1 bool + 6 floats if wanting sync (Syncs poorly even with this!), 1 bool if not (Compressable to 0 with VRCFury parameter - compress bools)
- Requires a controller to OSC Windows application (e.g. https://github.com/qbitzvr/VRCThumbParamsOSC )
- Left Thumbstick: Fwd/Backward/Left/Right
- Right Thumbstick: Pitch/Yaw
- Left/Right triggers: Up/Down
- B button: toggle Turbo Speed on/off
- REQUIRES SyncFix to drive the lens stealther (Lens automatically stealths for remote users when activating OSCcontrol)
- Current version designed for VRCLens v1.9.2


PRECONFIGURE:
- Choose weather or not you want to sync the controller parameters:
-- In the asset window, navigate to Assets/RaeCustoms/VRCLens_Custom/OSCController/OSCController_Params
-- Check (Or Uncheck) the 'Synced' box on every XInput* parameter depending on weather or not you want it to sync
--- DO NOT Unsync any non-XInput parameter (e.g. "OSCC_on")
--- Warning - this customisation will reset if you reimport a new RaeCustoms unitypackage


Steps:
1) Add the "RaeCustom_VRCLens_OSCController" prefab under your avatar root. It MUST BE LOWER Than SyncFix on the hierarchy!
1.1) If using alongside RootMount, you should avoid turning the two systems on together. The lowest system in the hierarchy should have control priority.
2) Navigate to "<avatar>/VRCLens/WorldC/CamPickup/CamBase"
3.1) On Object CamBase, Locate the Parent constraint.
3.1.1) By default, this parent constraint has THREE(3) Sources. If already using RootMount, it'll have FOUR(4) sources.
3.1.2) Add a FOURTH(4th) Source (If it doesn't exist) AND a FIFTH(5th) source.
3.1.3) Set the FOURTH(4th) and FIFTH(5th) source WEIGHT both to 0
3.1.4) Leave the FOURTH(4th) source either unset or set to RootMount if used.
3.1.4) Set the FIFTH(5th) source to "<avatar>/RaeCustom_VRCLens_OSCController/OSCC_root/OSCC_Base/OSCC_CamBase"

Done! Toggle on with menu path: VRCLens/Custom/OSCControl

Note: Check "Quick Checklist" at the top of this README if you're re-applying VRCLens! some steps must be repeated.


====================================================================
=========================== EXTRA TIPS =============================
====================================================================

1) Parent preview screen to Camera instead of Hand
- Want the Camera's preview to stay stuck to the camera mesh instead of your hand? 
-- Navigate to GameObject: <avatar>/VRCLens/WorldC/CamPickupAlways
-- Add a source to the existing Parent Constraint on this object (Below source DynVR)
-- Set the source to: <avatar>/VRCLens/WorldC/CamPickup/CamBase/CamObject
-- Set the source strength value of "DynVR" to 0
-- Set the source strength value of "CamObject" to 1
Done! If you reapply VRCLens, these steps must be repeated!

2) Customise the VRCLens Menu nondestructively
- Want to customise the VRCLens menu some? Place all your favorite/most used functions in the same menu?
-- You can use menu path VRCLens/Custom if you wish (This is used for VRCTally toggles/Smoothzoom)
-- You can add customisation ontop of the smoothzoom or syncfix prefabs on your avatar root if you wish
-- Add a VRCFury "Move or Rename Menu item" component.
-- Hit "Select" under "From Path" - find your target setting
-- Hit "Select" under "To Path" - Target your custom location (e.g. VRCLens/Custom) 
-- Add more of these components for each menu button you want to shortcut to.
Done!

3) Make the VR Hud preview of VRCLens render infront of everything (Prevent occlusion)
- Want the VRCLens HUD preview to stop being occluded by anything wandering infront of it? 
-- Navigate to the file; "Assets/Hirabiki/VRCLens/Resource/DepthOfFieldMeshPreview.shader"
-- Open this file in any text editor
-- Find the following section in the shader (Around Line 106);

-------------------- START OF CODE SNIPPET --------------------

		// PASS 3 ---- Should be totally possible to merge with PASS 2
		// Camera: [NONE] | VR: Head-Up Display
		Pass
		{
			
			CGPROGRAM
			#pragma vertex vert
			#pragma fragment frag
			#include "UnityCG.cginc"

-------------------- END OF CODE SNIPPET --------------------

-- Edit this section by adding an extra line (Line 106) and adding "ZTest Always":

-------------------- START OF CODE SNIPPET --------------------

		// PASS 3 ---- Should be totally possible to merge with PASS 2
		// Camera: [NONE] | VR: Head-Up Display
		Pass
		{
			ZTest Always
			
			CGPROGRAM
			#pragma vertex vert
			#pragma fragment frag
			#include "UnityCG.cginc"

-------------------- END OF CODE SNIPPET --------------------

Done! Save and close the file, and the VR Hud preview should no longer be occluded.