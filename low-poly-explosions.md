# unity-notes - LOW POLY EXPLOSIONS

In the scene :
    1. RIGHT_CLICK -) Effects -) Particle System
    2. Particle System component parameters :
        - Clicking on the name Explosion :
            - Duration : 2
            - Looping : Unchecked
            - Start Lifetime : 0.75
            - Start Speed : 30
            - Start Size : Random Between two constants (0.25 / 1)
            - Start Rotation : Random Between two constants (0 / 360)
        - Emission :
            - Rate Over Time : 1
            - Create new Burst (Count = 50, no other modifs to the params)
        - Shape :
            - Shape : Circle
            - Radius : 0.5
        - (Activate) Limit Velocity over lifetime :
            - Speed : 3
            - Dampen : 0.5
        - (Activate) Add a gradient of colors over Lifetime
            - Yellowish to Orangish
        - Renderer : 
            - Material : Square
        - (Activate) Size Over Lifetime :
            - Size : from top to bottom (preset)

have a look at https://www.youtube.com/watch?v=ig-0oJgy7NI&ab_channel=SingleSaplingGames			