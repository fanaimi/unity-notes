# unity-notes - camera following target

## have the camera following an object

```c#
public class CameraFollow : MonoBehaviour
{
    
    public Transform target; 	// the transform to follow
    public Vector3 offset;		// x, y, z, offset, distance from target
    
    // Update is called once per frame
    void Update()
    {
        transform.position = target.position + offset;
        transform.LookAt(target);
    }
    
}
```

