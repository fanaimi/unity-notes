# unity-notes - SINGLETON PATTERN

* prevents the creation of duplicates
* only one instance is possible at the same time

```c#
	/// <summary>
    /// singleton start
    /// </summary>
    private static Target _instance;
    public static Target Instance { get { return _instance; } }
    
    private void Awake()
    {
        if (_instance != null && _instance != this)
        {
            Destroy(this.gameObject);
        } else {
            _instance = this;
        }
    }
```
