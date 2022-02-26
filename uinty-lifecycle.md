# unity-notes - LIFECYCLE FUNCTIONS

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    // Recap
    // Awake - One approach is to init an objects own references and variables
    // Start - use or create rederences to other objects and their components


    // is called only once
    // is called when script is disabled
    // is called before the start
    // is called when other objects are initialized
    void Awake()
    {
        Debug.Log("Calling Awake");
    }

    // Start is called before the first frame update
    // is called when script is enabled
    // can be used as coroutine (execution of start can be delayed)
    void Start()
    {
        Debug.Log("Calling Start");
    }

    // is Called when script is enabled
    void OnEnable()
    {
        Debug.Log("Calling OnEnable");
    }

    void OnDisable()
    {
        Debug.Log("Calling OnDisable");
    }
	
	

	// is called on consistent frame rate
    // manipulate physics
    // for example: to manipulate "rigidbody" component
    void FixedUpdate()
    {
        Debug.Log("Calling Fixed Update");
    }



    // Update is called once per frame
    // is not consistent
    // one frame can take longer than other
    // you can use update:
    // to receive input from the user
    // do operation with timers
    // manipulate non physics objects
    void Update()
    {
        Debug.Log("Calling Update");
    }




    // is called after update
    // for example: manipulate camera
    void LateUpdate()
    {
        Debug.Log("Calling Late Update");
    }
}

```