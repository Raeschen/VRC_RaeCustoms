VRCLens Streaming/CamOps Addon Pack

PREREQUISITES:
-VRCLens (v1.9.2)
-VRCFury
-Poiyomi's Toon Shader

This pack consists of two parts;
- VRCLens "Blue Dragon" Camera model with Tally Light
- VRCLens "Sync Fix" tweak

Note: "Vector3()" values can be directly copied and pasted into XYZ fields to fill all three values at once.

====================================================================
======================= BLUE DRAGON CAMERA =========================
====================================================================

INFO:
1680 Tris
1 Material
Preconfigured Prefabs for VRCTally + shaders

PRECONFIGURE:
Shaders exist to put either an AudioLink animation or the video texture onto the middle-top settings screen on the base of the Blue Dragon Camera.
By default, the video texture version is applied to both prefabs.
Feel free to open the prefabs and change which shader is assigned!
Feel free also to edit the VRCTally VRCFURY parts on the root of the camera prefabs (i.e. the menu path, ect)
Do this BEFORE applying the camera as VRCLens UNPACKS the prefabs!

USAGE:
- Use VRC Lens as normal: Add the VRCLens main prefab to your scene.
- In the VRC Lens Setup Script;
-- Change the Camera Model to Blue Dragon Camera, either RearPreview (Preview screen on rear) or TopPreview(Preview screen on top)
-- Click "Change Camera Model"
-- Change field "Camera Scale" to 1
-- Change field "Preview Scale" to 0.155
-- Change field "Preview Position" to;
--- If using RearPreview: Vector3(0,0.0357,-0.515)
--- If using TopPreview: Vector3(0,0.233,-0.147)
-- The Preview screen will be tilted incorrectly - This is normal! We'll fix this later.
-- Position the Hand Camera and Head Camera however you wish. Helpful tip for Head Camera below!
--- You can place the Camera Prefab under "VRCLens/HeadMountPount" to sample how the headmount will look, BUT DELETE THE CAMERA PREFAB WHEN DONE!
-- Customise the remaining VRCLens settings and then apply VRCLens
- After applying VRCLens, look for the VRCLens Prefab under your avatar's root.
-- Navigate to YourAvatar/VRCLens/WorldC/CamPickupAlways/PreviewBase
-- Alter PreviewBase's Rotation to: Vector3(41,0,0)

Done! Either upload, or move on to SYNC FIX below.


====================================================================
============================ SYNC FIX ==============================
====================================================================

An Alteration to make VRCLens sync to remote players more securely.

Steps:
- Use VRCLens as normal, add it to an avatar
- After adding, add the "RaeCustom_VRCLens_SyncFix" prefab beneath the VRCLens object under your avatar, the one you just added
- Go to your Avatar's root. Check the Avatar Descriptor, navigate to the FX layer assigned.
- Open your base FX layer in the Animator tab.
- Delete the following animator layers;
-- vCNT_Base 225/254/255 i5
-- vCNT_Drop 250-252 [1B] i1,t23
-- vCNT_AttachSwap 223

Note: This MUST BE REPEATED when re-applying VRCLens! VRCLens will re-add the layers and remove the syncfix prefab when re-applying.

VRCLens should now sync it's state (On/off, hand/head/dropped/handrotating/avatarfixed) to remote users better.
