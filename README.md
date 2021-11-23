# unity-notes

## random notes about my XR, c# and unity journey 

### SETTING UP XR
* XR INTERACTION TOOLKIT
	* "com.unity.xr.interaction.toolkit": "1.0.0-pre.8"
	* import "Default Input Actions" and "XR device simulator"
	
* XR PLUG-IN MANAGEMENT
 
	Project settings > XR plugin management > PC> oculus and Windows mixed reality
 
	Project settings > XR plugin management > ANDROID > oculus 
 
* delete main camera
 
* XR > (Room Scale) XR Rig
 
* watch this video! https://www.youtube.com/watch?v=EWHOSbUIEwk&t=201s&ab_channel=SharkJets
 
* follow these steps:
	* on XR-rig > add component > Input Action Manager  
	* under Input Action Manager > Action assets >  size: 1 - Element 0: XRI Default Input Actions 
	* LeftHand Controller > remove component "XR Controller"
	* under Assets > samples > XR Interaction toolkit > v.v.v > Default Input actions, drag "" into LeftHand Controller
	* repeat for RightHand Controller
	
* for the ball:
	* sphere collider
	* rigidbody
	* XR Grab Interactable
	
* for Hands:
	* remove "XR Ray Interactor", "XR Interactor Line Visual" and "Line Renderer" 
	* add component "XR DIrect Interactor"
	* add "box collider" and scale to 0.1(x,y,z), set IsTrigger as true
	
* to avoiding seeiing through objects: 
	* main camera > Camera > Clipping planes > Near: 0.01
	
	
### GITATTRIBUTE AND LFS
	* to be added soon

### LIGHTING 	

####STATIC LIGHTING in unity
	* check this out: > https://www.youtube.com/watch?v=VnG2gOKV9dw&ab_channel=Brackeys
	
#### REALTIME LIGHTTING 
* SETTING UP REAL TIME LIGHTING
	* start from > https://www.youtube.com/watch?v=wwm98VdzD8s&ab_channel=Brackeys 
	* edit > project settings > player ==> other settings > rendering > color space > linear
	* main camera > allow HDR
	* main camera > rendering path > deferred
	* edit > project settings > quality
		* rendering > pixel light count > increase from 4 to 20
		
* POST PROCESSING
	* import "post processing stack" from git hub > com.unity.postprocessing
	* documentation > https://docs.unity3d.com/Packages/com.unity.postprocessing@2.1/manual/Quick-start.html?_ga=2.129568652.1681433161.1637588404-840189481.1633385198
	* also look at > https://www.youtube.com/watch?v=Ts2F2SxeRSY&t=1s&ab_channel=DitzelGames
	* create a new layer in main camera and call it "post processing"
	* main camera > add component > "post processing layer" > set layer as the one just created
	* create a new game object called "post processing" > add "post process volume" component
	* in assets > create > post processing profile
	* associate newly post processing profile in post process volume component in post processing game object
	* in postProcessing game object select layer > post processing
	* in postProccessing component use "GLOBAL" or create a box collider for partial areas
	* add effect > Color Grading
		* tone mapping > mode > filmic (ACES) 
		* tone > post exposure > .4
		
* LIGHTING 
	* ==> window > rendering > lighting 
	* lighting settings > new lighting settings (create a new one) 
	* real time lighting > Real time global illumination	
	* have a look at SKYBOX eg "free HDr sky"
	* lightning > environment > select "skybox material"
	* Environment lighting > source > gradient / color (chose black color for indoor scenes)
	
* LIGHT EMITTERS
	* start with DIRECTIONAL LIGHT (kinda like sun), play with SOFT SHADOWS, COLOR, INTENSITY
	* can use POINT LIGHT or SPOTLIGHT
	
* STATIC LIGHTS AND POST PROCESSING
	* create, size a position a plane
	* create a new material and call it glow-something :), drag it onto the plane
	* in the material, check "Emission", define a color
	* in post processing, select BLOOM effect and play with parameters
	* for each emitter, add a POINT LIGHT, set a color and play with range
	* still in POST PROCESSING, add a new effect "AMBIENT OCCLUSION", play with radius and intensity