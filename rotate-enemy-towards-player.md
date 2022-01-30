# unity-notes - ROTATE-ENEMY-TOWARDS-PLAYER

* rotating around Y AXIS ONLY

```c#
	// in ENEMY

	void Update()
    {
        RotateTowardsPlayer();
    }


    private void RotateTowardsPlayer()
    {
        if (!m_player)
        {
            return;
        }
        else
        {
            Vector3 m_targetDirection = m_player.transform.position - transform.position;
            Quaternion m_lookRotation = Quaternion.LookRotation(m_targetDirection);
			
            Vector3 m_rotation =
                Quaternion.Lerp(
                    transform.rotation,
                    m_lookRotation,
                    Time.deltaTime * m_turnSpeed
                ).eulerAngles;
            
            transform.rotation = Quaternion.Euler(0f, m_rotation.y, 0f);
        }
    } // RotateTowardsPlayer

```


