# unity-notes - raycasting

## creating a ray from an object into a certain direction

* useful eg to know if an object (enemy) sees another object (player) and it's not obstructed by obstacles
* can be used to calculate the direction of a projectile ricocheting from a surface calculating the normal of the surface
* a mask layer can be set to spcify which element we want to interact with 
* the ray interacts with the collider of the target so target must have a collider


### using Debug.DrawLine and changing colour of the ray
* Debug.DrawLine only works in the scene not in the game

```c#
public class Raycast1 : MonoBehaviour
{
    public  LayerMask mask;
    
    // Update is called once per frame
    void Update()
    {
        // RAYCAST constructors take 2 params: a vector3 origin and a vector 3 direction
        Ray ray = new Ray(
            transform.position,	// origin
            transform.forward	// direction
        );
        RaycastHit hitInfo;

        
		/**
		 * Physics.Raycast
		 * @param 	ray 			the ray to analyse
		 * @param 	hitInfo			information about what the ray hits (Struct, so we need OUT keyword)
		 * @param 	MaxDistance		max distance of the ray in meters, if not specified the ray goes on forever
		 * @param 	Layer			layer mask to interact with (ignoring elements that do not belong to this layer)
		 * @param   QueryTriggerInteraction 	interaction while collider is TRIGGER	[Collide/Ignore/useGlobal]
		 * @return  BOOL			hit or miss target
		 */
        if(Physics.Raycast(ray, out hitInfo, 100, mask) )
        {
            // 	 print(hitInfo.collider.name);
            //   Destroy(hitInfo.collider.gameObject);
            Debug.DrawLine(ray.origin, hitInfo.point, Color.red);
        } else {
            Debug.DrawLine(ray.origin, ray.origin + ray.direction * 100, Color.green);
        }

    } // update
    
} // Raycast1
```
* Edit > Project Settings > Physics => Query Hit Triggers [true/false]
* HITINFO stores, among other things, Collider, distance, normal of the surface that was hit, impact point etc

### using raycast to place an object on a terrain and change its rotation

```c#
public class Raycast2 : MonoBehaviour
{

    public Transform objectToPlace;
    public Camera gameCamera;
    
    

    // Update is called once per frame
    void Update()
    {
		// ray ffrom camera to where the mouse is
		// creen point is a position in pixels
		// THIS IS OLD INPUT!
        Ray ray = gameCamera.ScreenPointToRay(Input.mousePosition);

        RaycastHit hitInfo;

        if (Physics.Raycast(ray, out hitInfo) )
        {
            objectToPlace.position = hitInfo.point;
                // hitInfo.normal
                objectToPlace.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }

    }

} // Raycast2
```

* the normal is a vector perpendicular to the object hit, starting from the hitInfo.point
* objectToPlace.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal); [FROMdirection, TOdirection]


### using raycast in 2D

```c#
public class Raycast3 : MonoBehaviour
{

    /////// ADDED TO A 2D object
	
	void Start(){
		// this line prevents the raycast from hitting its own collider as it starts from its centre
		Physics2D.queriesStartColliders = false;
	}
    
    void Update()
    {;

        RaycastHit2D hitInfo = Physics2D.Raycast(
			transform.position, 	// origin
			transform.right,		// direction
			distance,				// lenght of ray
			ZminDepth,				// default: -infinite
			ZmaxDepth				// dafault: +infinite
		);

        if (hitInfo.Collider != null )
        {
            Debug.DrawLine(transform.position, hitInfo.point, Color.red)
        } 
		else 
		{
			Debug.DrawLine(transform.position, transform.position + transform.right * 100, Color.green)
		}

    }

} // Raycast3


```