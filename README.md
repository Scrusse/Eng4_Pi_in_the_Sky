# Pi_in_the_Sky

# Table of Contents

* [Schedule](#Schedule)
* [Designing](#Designing)
* [Functionablility and Materials](#Functionablility_and_Materials)

# Schedule
We must follow the schedule to a t for us to complete this by the end of the school year. WE first start working on our project just after Christmas break. 

From Janurary to End of Q2 - We finish initial CAD and code

From Q2 to March - We create a functional prototype

All through out March - We will do design refinement and final tweaks

All thorough out April - We make sure the drone launches and collects data

From May to when the drone is due - We analyze data that the drone collected and finish documentation of the drone

If needed after the due date we will have emergency project work time if we didnt finish


# Designing

## Initial Design
Our initial plan is to make a nuke shaped device that wil be launched and protect the ascent and decent of the rasberry pi. We also ended up making a onshape design so that we were able to compare it to all the components that we needed.
Initial design and reference picture:

<img src="https://user-images.githubusercontent.com/71342195/204313376-51ca5328-9db9-49df-b2a6-f57427667dd3.png" width="300px"><img src="https://user-images.githubusercontent.com/71342195/204315696-83aefc91-d7c2-400f-9384-0ba7efb19afa.png" width="200px"><img src="https://user-images.githubusercontent.com/71342195/204319456-e632d12b-2841-421b-b828-0732915cac08.png" width="400px">

## ReDesign
We ended up changing our design to a drone. As we are able to make our own circuitboard and we would be able to cut down on weight. It would also cut down on materials used as there was an excess use of ABP.
Here is our reference for a drone next to our initial design for our drone:

<img src="https://user-images.githubusercontent.com/71342195/204837447-9a0223bd-9544-4fe0-9009-91eb4449f9eb.png" width="400px"><img src="https://user-images.githubusercontent.com/71342195/206731486-579a0617-027c-4520-9d6a-464589515d7d.png" width="400px">

# Functionablility_and_Materials

## Functionability
Our plan to control this drone is to just let all of the motors go at full speed till we reach a certain height then turn them off. If we have time then we can change it so that mototrs rpm is slowly reduced till landing but first we have to make the drone work. 

Example of initial code: 

```python
# type: ignore

from operator import truediv
import adafruit_mpu6050 as imu
import busio
import board
import time
import pulseio



sdaPin = board.GP6  # defining the SDA & SCL pins to use
sclPin = board.GP7
i2c = busio.I2C(sclPin, sdaPin)
mpu = imu.MPU6050(i2c) 

motor1 = pulseio.PWMOut(board.GP2, frequency=1000, duty_cycle=0)
motor2 = pulseio.PWMOut(board.GP3, frequency=1000, duty_cycle=0)
motor3 = pulseio.PWMOut(board.GP4, frequency=1000, duty_cycle=0)
motor4 = pulseio.PWMOut(board.GP5, frequency=1000, duty_cycle=0)

#set motor speed
def set_motor_speeds(m1, m2, m3, m4):
    motor1.duty_cycle = m1
    motor2.duty_cycle = m2
    motor3.duty_cycle = m3
    motor4.duty_cycle = m4

#get acceleration from accelerometer
def get_acceleration():
    x, y, z = accel.acceleration
    return x, y, z



while True:
    x, y, z = get_acceleration()

    #adjust motor speeds based on acceleration
    motor1_speed = -x
    motor2_speed = -y
    motor3_speed = z
    motor4_speed = -z

    #set motor speeds
    set_motor_speeds(motor1_speed, motor2_speed, motor3_speed, motor4_speed)

    #wait
    time.sleep(.1)

    accelerationVals = mpu.acceleration
    
    print(f"X acceleration: {accelerationVals[0]} m/s2")
    print(f"Y acceleration: {accelerationVals[1]} m/s2")
    print(f"Z acceleration: {accelerationVals[2]} m/s2")
    print("")
    time.sleep(.1)
```



## Risk Mitigation
There isnt much risk involving drones since there isnt any presssure, liquids, or harsh chemicals. The only thing that we would need to watch out for would be the drone blades as there isnt much stopping it from protecting the surroundings. To protect us from the blades we would need to make sure that we arent touching the drone when it takes off or if the blades are spinning at all.

## Materials
Some of the materials and supplies that we need are easy to ge as we have them here in the lab. The other supplies would need to be ordered. Here is a list of all of our supplies include: 4 dc coreless motors, circuitboard, accelerometer (MPU6050), battery pack, altimeter (MPL3115A2), GPS module, 2 H-bridges, a powerboost, and 3d printed/lasercut supplies. We would need to buy 4 dc motors, a 1300 mAh battery, and a GPS module. As those are the only things that we dont have in the lab.
