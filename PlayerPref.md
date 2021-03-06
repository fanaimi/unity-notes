# unity-notes - SAVING AND GETTING SAVED DATA - PlayerPref



* read documentation [here](https://docs.unity3d.com/ScriptReference/PlayerPrefs.html)

* AT THE VERY TOP creating a Struct, faster and more efficient to store data

```c#

// datatype to quickly get data, data saved in memory with precise location
 public struct SaveData
 {
	public int score;
	public int numOfLives;
 }



* saving ( eg: OnApplicationQuit )

```c#
    public void SetHighScore(int score)
    {
        // creating a SaveData obj
        SaveData saveData = new SaveData();

        // populating SaveData obj
        saveData.sd_highScore = score;

        // serialising SaveData with JSON
        string savedJSON = JsonUtility.ToJson(saveData);

        // saving JSON to PlayerPref
        PlayerPrefs.SetString("runesData", savedJSON);

        m_highScore = score;
    }
	
```




* loading (in Awake)

```c#

	   public int GetHighScore()
    {
        // getting JSON to PlayerPref
        string savedJSON = PlayerPrefs.GetString("runesData");

        // deserialising JSON into SaveData obj
        SaveData saveData = JsonUtility.FromJson<SaveData>(savedJSON);

        // populating game data with SaveData obj
        m_highScore = saveData.sd_highScore;

        return m_highScore;
    }

```



* how to find PLAYER PREFS data in WINDOWS 

```c#
	{regedit}
	registry editor > HKEY_CURRENT_USER > SOFTWARE > Unity > 
	{company name} DefaultCompany > gameName

```

* how to find PLAYER PREFS data in MAC 

```c#
	/Library/Preferences/Unity.DefaultCompany.{projectname}.plist

```