# unity-notes - get mouse position 2d

## getting mouse position 
### the Camera MUST have a tag of "MainCamera"
#### Camera.main.ScreenToWorldPoint(Input.mousePosition)

```c#
public class SomeClass : MonoBehaviour
{
    
	
	// getting position 
	private void OnMouseDrag()
    {
        Vector3 m_mousePos = Camera.main.ScreenToWorldPoint(Input.mousePosition);
        transform.position = new Vector3(m_mousePos.x, m_mousePos.y, transform.position.z);
    } // OnMouseDrag
	
 
    // [...]
}
```

### getting direction and adding force
```c#
public class SomeClass : MonoBehaviour
{
	// [...]

    private void OnMouseUp()
    {
        // Debug.Log("mouse up");
        m_spriteRend.color = Color.white;
		
        Vector2 m_currentPos = m_rb.position;

        Vector2 m_direction = m_startPos - m_currentPos;
        m_direction.Normalize();
        
		m_rb.isKinematic = false;
        m_rb.AddForce(m_direction * m_speed);
    } // OnMouseUp

```
