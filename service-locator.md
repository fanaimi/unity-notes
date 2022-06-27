# unity-notes - SERVICE LOCATOR PATTERN

* CAN BE AN ANTI-PATTERN



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

** SERVICE LOCATOR
```c#
// ServiceLocator.cs
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ServiceLocator : Singleton<ServiceLocator> {

    private IDictionary<Type, MonoBehaviour> serviceReferences;
    protected void Awake() {
        SingletonBuilder( this );
        serviceReferences = new Dictionary<Type, MonoBehaviour>();
    }

    public T GetService<T>() where T : MonoBehaviour, new() {
        UnityEngine.Assertions.Assert.IsNotNull( serviceReferences, "Someone has requested a service prior to the locator's intialization." );

        bool serviceLocated = serviceReferences.ContainsKey( typeof( T ) );
        if ( !serviceLocated ) {
            serviceReferences.Add( typeof( T ), FindObjectOfType<T>() );
        }

        UnityEngine.Assertions.Assert.IsTrue( serviceReferences.ContainsKey( typeof( T ) ), "Could not find service: " + typeof( T ) );
        var service = ( T ) serviceReferences [ typeof( T ) ];
        UnityEngine.Assertions.Assert.IsNotNull( service, typeof( T ).ToString() + " could not be found." );
        return service;
    }
}


```