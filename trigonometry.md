# unity-notes - TRIGONOMETRY

* problems: getting directions from angles and angles from directions
* getting radians from degrees and vice versa

## we know the angle (a), we want coordinates of the point on the circle (x,y)
* 
```c#
	y = sin(a)
	x = cos(a)
	VECTOR = (cos(a), sin(a))
```


* the plots of sin and cos are identical but offset by 90degrees
```c#
sin(a) = cos(90-a)
cos(a) = sin(90-a)
tan(a) = sin(a) / cos(a)
```

## we know x and y of the vector, we need the angle
```c#
a = atan2(y,x)
```




## converting deg to rad and rad to deg
* 
```c#
rad = deg * (PI/180)
deg = rad * (180/PI)


```

## UNITY CIRCLE is not the same as TRIG CIRCLE
* so we need some conversion  
```c#
angle = 90 - unityAngle

unityAngle = 90 - angle

```


## UNITY TRIG, getting direction from angle 
### calculations are computed in RADIANS! 
### Sin and Cos are swapped because of the 90deg-angle due to the difference in the Unity circle
```c#
	public float angleInDeg;

	void Update(){
		Vector3 direction = new Vector3( 
			Mathf.Sin(angleInDeg * Mathf.Deg2Rad), 
			0,  
			Mathf.Cos(angleInDeg * Mathf.Deg2Rad), 
		);


		Debug.DrawRay(startPosition, direction*distance, color);
	}


```




## UNITY TRIG, getting angle from direction 
### calculations are computed in RADIANS! 
* gettin input from arrow keys and calculatin the angle
```c#
	public float angleInDeg;

	void Update(){
		Vector3 direction = new Vector3( 
			Mathf.Sin(angleInDeg * Mathf.Deg2Rad), 
			0,  
			Mathf.Cos(angleInDeg * Mathf.Deg2Rad), 
		);
		Debug.DrawRay(startPosition, direction*distance, color);

		// getting direction from keyboard
		Vector3 inputDir = 
			new Vector3(Input.GetAxisRaw("horizontal"), 0, Input.GetAxisRaw("vertical")).normalise;

		// moving player	
		transform.Translate(inputDir * Time.deltaTime * 5, Space.World);

		// rotating player, we need the angle or rotation atan2(y, x) 
		// **** but we need 90deg-a OR WE FLIP atan2*(x,y) 
		float inputAngle = 90 - Mathf.atan2(inputDir.x, inputDir.z) * Mathf.rad2deg;

		// then we can apply rotation aroung V3.up (y axes)
		transform.eulerAngles = Vector3.up * inputAngle;

	}


```
