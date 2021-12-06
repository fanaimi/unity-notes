# unity-notes - COROUTINES

* coroutines belong to UNITY, not C#
* can be used to be paused using "yield"
* coroutines stop and restart at the next frame
* during pauses, the rest of the code will execute
* pauses can be longer using WaitForSeconds(number of seconds)


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