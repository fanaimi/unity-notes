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
        renderer.material.color = Color.red;
    }
}
```

### Using Color.Lerp() to transition from a color to another
```c#
public class AnotherClass
{
	// the game object 
	[SerializeField] GameObject el;

	// lerping timer
	[SerializeField] [Range(0f, 1f)] float lerpTime;
    
	// its mesh renderer
    private MeshRenderer renderer;

	// empty var to get color
    private Color defaultColor;

	void Start()
    {
		// getting the mesh renderer
        renderer = el.GetComponent<MeshRenderer>();

		// setting a new color
        renderer.material.color = Color.red;
    }

	void Update()
	{
		renderer.material.color = Color.Lerp(renderer.material.color, Color.blue, lerpTime * Time.deltaTime);
	}

}
```