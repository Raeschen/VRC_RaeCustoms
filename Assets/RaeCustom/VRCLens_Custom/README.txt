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

VRCLens should now sync it's state (On/off, hand/headm dropped/handrotating/avatarfixed) to remote users better.
