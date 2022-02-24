# unity-notes - COUNTDOWN-TIMER


** subtracting Time.deltaTime from timeLeft
```c#

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class TimerController : MonoBehaviour
{
    public float m_timeLeft = 60f;
    private bool m_timerActive = false;

    private static TimerController _instance;
    public static TimerController Instance { get { return _instance; } }

    private void Awake()
    {
        // Debug.Log("awakening");
        if (_instance != null && _instance != this)
        {
            Destroy(this.gameObject);
        }
        else
        {
            _instance = this;
        }
        
    }

    
    void Start()
    {
        m_timerActive = true;
    }

    // Update is called once per frame
    void Update()
    {
        if (m_timerActive)
        {
            if (m_timeLeft > 0)
            {
                m_timeLeft -= Time.deltaTime;
                UIcontroller.Instance.ShowTimeLeft(m_timeLeft);
            }
            else
            {
                m_timeLeft = 0;
                m_timerActive = false;
                GameManager.Instance.ShowGameOver();
            }
        }
    }
}

```

** converting float into int before displaying into UI:
```c#
	int scoreINT = Mathf.RoundToInt(scoreFLOAT);
	m_someUIfield.text = scoreINT.ToString();

```