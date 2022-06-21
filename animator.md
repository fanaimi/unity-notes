# unity-notes - ANIMATOR

## triggering animation using cached animation name
* store collections of a fixed size
```c#
Class someClass {
	// caching trigger event name into an int
	static readonly int EVENT_NAME = Animator.StringToHash("event_name";)
	[SerializeField] Animator m_animator;

	void OnValidate() => m_animator = GetComponent<Animator>();

	void SomeFoo()
	{
		m_animator.SetTrigger(EVENT_NAME);
	}
}	
```

