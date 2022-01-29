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
    }
	
	public void SomeMethod(){}
	
```

* to access, just use
```c#
	SomeManager.Instance.SomeMethod();
```