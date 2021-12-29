# unity-notes - changing colours

```c#
public class SomeClass
{
	// the game object 
	[SerializeField] GameObject el;
    
	// its mesh renderer
    private MeshRenderer renderer;

	// empty var to get color
    private Color defaultColor;

	void Start()
    {
		// getting the mesh renderer
        renderer = el.GetComponent<MeshRenderer>();

		// getting the color
		defaultColor = renderer.material.color;

		// setting a new color
        renderer.material.color = Color.red;;
    }

}


```