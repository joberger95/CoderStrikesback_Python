BERGER Jordan

https://www.codingame.com/profile/c6231376e80897d910854f3a03b9e8117380273

# Journal de bord



Passage de la Ligue BOIS à la ligue BRONZE. 

```Python
    import sys
    import math

    while True:
        
        x, y, next_checkpoint_x, next_checkpoint_y, next_checkpoint_dist, next_checkpoint_angle = [int(i) for i in input().split()]
        opponent_x, opponent_y = [int(i) for i in input().split()]
        
        if next_checkpoint_angle > 90 or next_checkpoint_angle < -90:
            thrust = 0
        else:   
            if next_checkpoint_dist > 2000:
                thrust = "BOOST"
            else:
                thrust = 100
                
        print(str(next_checkpoint_x) + " " + str(next_checkpoint_y) + " " + str(thrust))  
```
13h00

Il est prévu que je passe à la ligue suivante dans 35 minutes, soit la Ligue ARGENT. Je n'ai fait qu'une très légère modification. On remarque aussi le morceau en commentaire qui avait pour lieu d'être un test. Le programme actif est celui ci-dessous. 

```Python
import sys
import math

while True:
   
    x, y, next_checkpoint_x, next_checkpoint_y, next_checkpoint_dist, next_checkpoint_angle = [int(i) for i in input().split()]
    opponent_x, opponent_y = [int(i) for i in input().split()]
    
    if next_checkpoint_angle > 90 or next_checkpoint_angle < -90:
        thrust = 0
    else:
        if next_checkpoint_dist > 4000:# and opponent_y == 400 and opponent_x == 400:
            thrust = "BOOST"
        else:
            thrust = 100
            
    print(str(next_checkpoint_x) + " " + str(next_checkpoint_y) + " " + str(thrust)) 
```





```Python
import sys
import math

#Debug tool (from V.POULALLEAU)
def debug(*args, **kwargs):
    print(*args, **kwargs, file=sys.stderr)

#Opponent proximity
def opponent_proximity( x , y , opponent_x , opponent_y ):
    pod = ( opponent_x - x )**2
    pod_opponent = ( opponent_y - y )**2
    square_of_sum = math.sqrt(pod + pod_opponent)
    debug(square_of_sum)
    return square_of_sum
# Auto-generated code below aims at helping you parse
# the standard input according to the problem statement.

#Globals variables
available_boost = True
# game loop
while True:
    # next_checkpoint_x: x position of the next check point
    # next_checkpoint_y: y position of the next check point
    # next_checkpoint_dist: distance to the next checkpoint
    # next_checkpoint_angle: angle between your pod orientation and the direction of the next checkpoint
    x, y, next_checkpoint_x, next_checkpoint_y, next_checkpoint_dist, next_checkpoint_angle = [int(i) for i in input().split()]
    opponent_x, opponent_y = [int(i) for i in input().split()]
   
    # Write an action using print
    # To debug: print("Debug messages...", file=sys.stderr)

    # You have to output the target position
    # followed by the power (0 <= thrust <= 100) or "BOOST"
    # i.e.: "x y thrust
    if next_checkpoint_angle <= 90 or next_checkpoint_angle >= -90:
        if next_checkpoint_dist > 1000:
            thrust = 100
        if next_checkpoint_dist > 750 and next_checkpoint_dist <= 1000:
            thrust = 50
        if next_checkpoint_dist < 250:
            thrust = 25 
            
    if next_checkpoint_angle > 90 or next_checkpoint_angle < -90:
        thrust = 15
        
    if next_checkpoint_dist > 1000 and  available_boost == True:
        thrust = "BOOST"
        available_boost = False
        
    pods_dist_diff=opponent_proximity(x , y , opponent_x , opponent_y)
    if pods_dist_diff <= 450:
        thrust = "SHIELD"
        
    print(str(next_checkpoint_x) + " " + str(next_checkpoint_y) + " " + str(thrust)) 
    debug(thrust)
```