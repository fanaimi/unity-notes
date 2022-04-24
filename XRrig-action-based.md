# unity-notes - XRrig action based

## XR-rig
* install XR Interaction toolkit and samples
* install XR Plugin Management
	* Project Settings > XR Plugin Management > check Oculus
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
* XR Origin -> add component "Teleportation Provider"	
	* drag Locomotion System component under Teleportation Provider (Script) > System
* if necessary, drag XRI Default Snap Turn  (project panel > Assets > Samples > XR Interaction Toolkit > V.v.v > Starter Assets) as a component of XR Origin 
	* drag Locomotion System component under Snap Turn Provider (action-based) > System


## for controllers:
* drag XRI Default Left Controller (project panel > Assets > Samples > XR Interaction Toolkit > V.v.v > Starter Assets) under XR Origin > LeftHand Controller > XR controller (Action-based) 	
* repeat for right controller
* we can turn LeftHand Controller into "LeftHand Teleportation Controller"
	* create Camera Offset > new > XR >  Direct Interactor (Action-based) -> rename it as LeftHandGrabController 
		* drag XRI Default Left Controller (project panel > Assets > Samples > XR Interaction Toolkit > V.v.v > Starter Assets) under XR Origin > LeftHandGrabController > XR controller (Action-based)
* make LeftHand Teleportation Controller a child of LeftHandGrabController		
	* under LeftHand Teleportation Controller > XR controller (Action-based)
		* uncheck "Enable Input Tracking"
		* uncheck "Position Action > Use Reference"
		* uncheck "Rotation Action > Use Reference"		

* under LeftHandGrabController, create new empty object -> Model Parent
	* drag hand model under Model Parent

* under LeftHand Teleportation Controller > XR controller (Action-based)
	* Under Activate Action > Reference => replace "XRI LeftHandActivate" with "XRI LeftHand/Teleport Mode Activate"

* REPEAT FOR RIGHT HAND :)
* good to make XR Origin with all these settings as a PREFAB so it's easy to import/export it


## for grabbable objects:
* add Rigid Body and box collider
* add component "XR Grab Interactable"

## for events:
```c#
// usegul namespaces to add
using System;
using UnityEngine.Events;
using UnityEngine.XR.Interaction.Toolkit;

public class MyClassInteractable : XRBaseInteractable
{
	// inheriting from UnityEvent, expecting a float param
	[Serialisable]
	public class MyCustomEvent<float> : UnityEvent {}

	// creating the event => it will appead in the inspector like UI button click 
	public MyCustomEvent OnMyEventHappened;

}

```
