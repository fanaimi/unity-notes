# unity-notes - PLAYER ROTATION

```c#
void update(){
	Vector3 inputDirection = new Vector3(
		Input.GetAxisRaw("Horizontal"), 
		0,
		Input.GetAxirRaw("Vertical")
	).normalized;


	float targetAngle = Mathf.atan2(InputDirection.x, InputDirection.z) * Mathf.Rad2Deg;
	
	transform.eulerAngles = Vector3.up * targetAngle;


}


```