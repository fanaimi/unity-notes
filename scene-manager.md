# unity-notes - SCENE MANAGER

* load namespace at the top
```c#

using UnityEngine.SceneManagement;

```


* loading a scene 
```c#

SceneManager.LoadScene($"{m_scene-to-load}");
```

* reloading current scene
```c#
	Scene scene = SceneManager.GetActiveScene();
	  
	SceneManager.LoadScene(scene.name);

```

