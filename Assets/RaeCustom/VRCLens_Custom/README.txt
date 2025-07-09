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
- Usage of VRCFury "Parameter Compressor" is RECOMMENDED to save sync-bits without having to remove stuff.


QUICK CHECKLIST IF UPDATING/REAPPLYING VRCLENS AFTER ADDING THESE ADDONS:
> Re-set GameObject <avatar>/VRCLens/WorldC/CamPickupAlways/PreviewBase Rotation X to 41 ( Vector3(41,0,0) )
> Make sure all addon prefabs exist
> Re-check Avatar Base FX layer - Remove all layers corresponding to addons (SyncFix:Step 5, SmoothZoom: Step 5)


INSTALLATION:
====================================================================
======================= BLUE DRAGON CAMERA =========================
====================================================================

INFO:
Top:1458, Rear:1466 Tris
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
2.3) Change field "Camera Scale" to 1
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

Done! Either upload, or move on to SYNC FIX below.


====================================================================
============================ SYNC FIX ==============================
====================================================================

An Alteration to make VRCLens sync to remote players more securely.

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

Note: This MUST BE REPEATED when re-applying VRCLens! VRCLens will re-add the layers and remove the syncfix prefab when re-applying.

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

Note: This MUST BE REPEATED when re-applying VRCLens! VRCLens will re-add the layers and remove the syncfix prefab when re-applying.

VRCLens should now zoom (Both with zoom buttons and with the zoom radial under VRCLens/Custom) much more smoothly