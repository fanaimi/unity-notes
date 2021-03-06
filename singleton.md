# unity-notes - SINGLETON PATTERN

* prevents the creation of duplicates
* only one instance is possible at the same time
* can be accessed anywhere without instantiation or reference

```c#
	/// <summary>
    /// singleton start
    /// </summary>
    private static SomeManager _instance;
    public static SomeManager Instance { get { return _instance; } }
    
    private void Awake()
    {
        if (_instance != null && _instance != this)
        {
            Destroy(this.gameObject);
        } else {
            _instance = this;
        }

        // if we want this to survive throughout different levels and scenes
        DontDestroyOnLoad(gameObject);

    } // Awake
	
	public void SomeMethod(){}
	
```

** to access, just use
```c#
	SomeManager.Instance.SomeMethod();
```


* singleton abstract class to inherit from (from https://www.mrventures.net/)
```c#
// Singleton.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public abstract class Singleton<T> : MonoBehaviour
{
    private static T _instance;
    public static T instance
    {
        get
        {
            if (Equals(_instance, null) || _instance == null || _instance.Equals(null))
            {
                var instanceGO = FindObjectOfType<Singleton<T>>();
                _instance = instanceGO.GetComponent<T>();
                return _instance;
            }
            else
            {
                return _instance;
            }
        }
        set { _instance = value; }
    }

    // The child must call SingletonBuilder() with a reference to itself.
    protected void SingletonBuilder(T newInstance)
    {
        // If another already exists, forget this one
        var instanceGO = FindObjectsOfType<Singleton<T>>();
        if (instanceGO.Length > 1)
        {
            Destroy(this.gameObject);
            return;
        }

        if (_instance == null)
        {
            _instance = newInstance;
        }
        else if (_instance.Equals(newInstance))
        {
            Debug.LogWarning("Found two singletons of type " + this);
            Destroy(gameObject);
        }
    }
}

```

** to inherit from abstrac class (check service locator) 
```c#

public class MyManager : Singleton<MyManager> {

   
}

```