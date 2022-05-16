# unity-notes - CUSTOM EVENTS - OBSERVER PATTERN

## sending notifications and decoupling observer/observed

### observed (eg: a player)
```c#

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;
using System;


public class Player : MonoBehaviour
{
	// creating the event
    public event Action OnSomethingCustom;
    
	
	void Start()
    {
        if(conditionsApply)
		{
			TriggerOwnCustomEvent();
		}
    }
	
	private void  TriggerOwnCustomEvent()
	{
		// if anyone is listening
		if (OnSomethingCustom != null )
		{
			// trigger the custom event
			OnSomethingCustom();
		}
	}
}

```



### observer (eg: a manager)
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;
using System;


public class UIcontroller : MonoBehaviour
{

    void Start()
    {
		// subscribing listener to event
        Player.OnSomethingCustom += ReactToEvent;
    }

	// listener
    private void ReactToEvent()
    {
        // doing something fancy as a reaction
    }
	
	
    private void OnDisable()
    {
		// unsubscribing
        Player.OnSomethingCustom -= ReactToEvent;
    }
	
}

```

