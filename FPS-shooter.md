# unity-notes - FPS shooter, move with keyboard, look with mouse

```c#
using UnityEngine;

public class FPSController : MonoBehaviour
{
    [SerializeField] private float movementSpeed = 10;
    [SerializeField] private float mouseSensitivity = 1;
    [SerializeField] private float minXRotation = -60;
    [SerializeField] private float maxXRotation = 60;

    [SerializeField] private string horizontalAxisInput = "Horizontal";
    [SerializeField] private string verticalAxisInput = "Vertical";

    [SerializeField] private Transform cameraTransform;

    private float verticalRotation;

    private void Move()
    {
        // Get the player input with the GetAxis method:
        // https://docs.unity3d.com/ScriptReference/Input.GetAxis.html
        // You can configure which keys control the axis from the Input Manager:
        // https://docs.unity3d.com/Manual/class-InputManager.html
        float horizontalInput = Input.GetAxis(horizontalAxisInput);
        float verticalInput = Input.GetAxis(verticalAxisInput);

        Vector3 movementDirection = new Vector3(horizontalInput, 0, verticalInput);
        // We normalize the vector to make sure it has a magnitude of 1
        // This way we can multiply it by speed and get consistent velocities.
        movementDirection.Normalize();

        transform.Translate(movementDirection * movementSpeed * Time.deltaTime, Space.Self);
    }

    // Take a look at the Player GameObject hierarchy before reading this method
    private void LookAtMouse()
    {
        // When using the GetAxis with a mouse, the return value is different from keyboard buttons:
        // https://docs.unity3d.com/ScriptReference/Input.GetAxis.html
        transform.Rotate(new Vector3(0, Input.GetAxis ("Mouse X") * mouseSensitivity, 0));

        // This first piece of code rotates horizontally the root transform of the player
        // We separate the vertical rotation to a child object that holds the camera
        // This way we can still use the Translation in local space (line 31) without having the
        // vertical rotation break our movement.

        verticalRotation -= mouseSensitivity * Input.GetAxis("Mouse Y");
        // We clamp the rotation so the player can't fully rotate vertically
        verticalRotation = Mathf.Clamp(verticalRotation, minXRotation, maxXRotation);
        cameraTransform.localEulerAngles = new Vector3(verticalRotation, 0, 0);
    }

    private void Update()
    {
        LookAtMouse();
        Move();
    }

    private void Awake()
    {
        Cursor.lockState = CursorLockMode.Locked;
        Cursor.visible = false;
    }
}
```
