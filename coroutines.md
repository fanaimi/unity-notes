# unity-notes - COROUTINES

* Coroutines allow spreading the execution of code ove multiple frames using "yield return"
* coroutines belong to UNITY, not C#
* can be used only within classes that inherit from Monobehaviour
* coroutines stop and restart at the next frame
* during pauses, the rest of the code will execute


```c#
	void Start() {
		StartCoroutine(DoSomething);
	}
	
	IEnumerator DoSomething() 
	{
		while(true){
			yield return new WaitForSeconds(.5f); // will wait for .5 secs and the restof the code will be executed
		}
	}
	
```

* coroutine to move 
```c#
	void Start()
	{
		StartCoroutine(Move);
	}
	
	
	IEnumerator Move(Vector3 destination, float speed) 
	{
		while(transform.position != destination)
		{
			transform.position = Vector3.MoveTowards (transform.position, destination, speed * Time.deltaTime);
			yield return null; // wait  until next frame
		}
	}

```

* can be paused until next frame using 
``` 
yield return null
```

* pauses can be longer using 
```
yield return new WaitForSeconds(number of seconds)
```

* pause until the coroutine has finished running using 
```
yeld return StartCoroutine(DoSomething())
```

* coroutines can be stopped using StopCoroutine() method
```
IEnumerator someCoroutine = DoSomething();
StartCoroutine(someCoroutine);
StopCoroutine(someCoroutine);
```			
