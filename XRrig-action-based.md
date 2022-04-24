# unity-notes - XRrig action based

## XR-rig
* install XR Interaction toolkit and samples
* hierarchy > UI > XR > Xr Origin (Action-based)
* XR Origin > add component > Input Action Manager 
* under Input Action Manager, increase Action Assets to 1
* drag XRI Default Input Actions (project panel > Assets > Samples > XR Interaction Toolkit > V.v.v > Starter Assets) under XR Origin > Input Action Manager > Action Assets

## for teleportation: 
* make sure floor has a box collider
* add new layer to floor, eg teleportation
* add component to floor: Teleportation area
* XR Origin -> add component "Locomotion System"
	* drag XR Origin (script) component under Locomotion System > XR Origin 
* if necessary, drag XRI Default Snap Provider  (project panel > Assets > Samples > XR Interaction Toolkit > V.v.v > Starter Assets) as a component of XR Origin 