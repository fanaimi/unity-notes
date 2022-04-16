# unity-notes - TMP

* working with TMP text 


## namespace, declaration, populating 
* 
```c#
	// namespace
	using TMPro;
    // declaration
	[SerializeField] private TMP_Text m_someText;
	// populating
	m_someText.text = somevalue;
```



## converting numbers into strings 
```c#
	m_someText.text = someNumber.ToString();
```

## converting strings into integers
```c#
	int someInt = int.Parse(m_someText.text);
```

## converting strings into float
```c#
	float someFloat = float.Parse(m_someText.text);
```





