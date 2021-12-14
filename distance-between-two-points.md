# unity-notes - DISTANCE BETWEEN TWO POINTS

* easy to calculate with Vector3.Distance

## we know the angle (a), we want coordinates of the point on the circle (x,y)
```c#
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    public Transform other;

    void Example()
    {
        if (other)
        {
            float dist = Vector3.Distance(other.position, transform.position);
            print("Distance to other: " + dist);
        }
    }
}


```
