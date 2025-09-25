# Ex-1-Developing-AI-Agent-with-PEAS-Description

**Name:** Gowtham S

**Register Number:** 2305002008

## Aim:

To find the PEAS description for the given AI problem and develop an AI agent.

## Theory :

PEAS stands for:
```
P-Performance measure

E-Environment

A-Actuators

S-Sensors
```

It’s a framework used to define the task environment for an AI agent clearly.


## Pick an AI Problem


**1.** Self-driving car

**2.** Chess playing agent

**3.** Vacuum cleaning robot

**4.** Email spam filter

**5.** Personal assistant (like Siri or Alexa)

## Developing AI Agent with PEAS Description – Self-Driving Car Agent

### Agent: Self-Driving Car Agent (Environment-based, action-driven)

**Performance Measure:**

1. Reaches destination safely without accidents.

2. Minimizes travel time.

3. Obeys traffic rules (signals, speed limits).

4. Avoids collisions with obstacles, pedestrians, and other vehicles.

5. Maintains passenger comfort (smooth driving, not excessive braking).

**Environment:**

1. Road networks (lanes, intersections, turns).

2. Dynamic traffic lights (Red, Yellow, Green).

3. Obstacles such as pedestrians, other vehicles, animals, or debris.

4. Weather and road conditions (rain, fog, potholes).

5. Fully observable through sensors, but dynamic and partially unpredictable.

**Actuators:**

1. Steering wheel (left/right turns).

2. Accelerator (increase speed).

3. Brake (decrease/stop speed).

4. Gear system (forward, reverse, neutral).

5. Indicators/Horn (optional for communication with environment).

**Sensors:**

1. Cameras (lane detection, traffic light recognition, pedestrian detection).

2. LiDAR/Radar (detects obstacles and distance from objects).

3. GPS (location tracking and navigation).

4. Speedometer (current speed).

5. Proximity sensors (close-range obstacle detection).

## Algorithm:

**Step 1:** Initialize the car’s state with: Starting location, destination, speed = 0 ;Environment conditions (traffic light = Green, no obstacles) ;Set move counter = 0.

**Step 2:** Define the possible actions for the car: Accelerate, Brake, Stop, Steer Left, Steer Right, Do Nothing.

**Step 3:** Repeat the following steps until the car reaches its destination:

3.1. Sense the environment (check traffic light, detect obstacles, update speed).

3.2. If the traffic light is Red, stop the car.

3.3. If the traffic light is Yellow, slow down (brake).

3.4. If the traffic light is Green, accelerate forward.

3.5. If an obstacle is detected, steer to avoid it and brake.

3.6. Record the last action taken.

3.7. Increment the move counter by one.

3.8. Optionally, display the last action and current status (location, speed, traffic light, obstacle status).

**Step 4:** Stop the loop when the car reaches its destination safely.

**Step 5:** Declare success (trip completed) or failure (accident, unable to proceed).

**Step 6:** Optionally, print a summary of total moves and sequence of actions performed.

### Example Program:
```
class VacuumCleanerAgent:
    def __init__(self):
        # Initialize the agent's state (location and dirt status)
        self.location = "A"  # Initial location (can be "A" or "B")
        self.dirt_status = {"A": False, "B": False}  # Initial dirt status (False means no dirt)

    def move_left(self):
        # Move the agent to the left if possible
        if self.location == "B":
            self.location = "A"

    def move_right(self):
        # Move the agent to the right if possible
        if self.location == "A":
            self.location = "B"

    def suck_dirt(self):
        # Suck dirt in the current location if there is dirt
        if self.dirt_status[self.location]:
            self.dirt_status[self.location] = False
            print(f"Sucked dirt in location {self.location}")

    def do_nothing(self):
        # Do nothing
        pass

    def perform_action(self, action):
        # Perform the specified action
        if action == "left":
            self.move_left()
        elif action == "right":
            self.move_right()
        elif action == "suck":
            self.suck_dirt()
        elif action == "nothing":
            self.do_nothing()
        else:
            print("Invalid action")

    def print_status(self):
        # Print the current status of the agent
        print(f"Location: {self.location}, Dirt Status: {self.dirt_status}")
```

### Example usage:

```
agent = VacuumCleanerAgent()
```

### Move the agent, suck dirt, and do nothing

```
agent.perform_action("left")
agent.print_status()
agent.perform_action("suck")
agent.print_status()
agent.perform_action("nothing")
agent.print_status()
```

### Sample Output:

<img width="570" height="77" alt="image" src="https://github.com/user-attachments/assets/70bf8483-1b65-46d6-ab8b-eeda6d591f36" />


## Program:

```
class SelfDrivingCarAgent:
    def __init__(self):
        # Initialize the car's state
        self.location = "Home"
        self.destination = "Office"
        self.speed = 0  # in km/h
        self.obstacles = False
        self.traffic_light = "Green"  # can be "Red", "Yellow", "Green"

    # ----- Actuators -----
    def accelerate(self):
        self.speed += 10
        print(f"Accelerating... Speed = {self.speed} km/h")

    def brake(self):
        if self.speed > 0:
            self.speed -= 10
        print(f"Braking... Speed = {self.speed} km/h")

    def stop(self):
        self.speed = 0
        print("Car stopped.")

    def steer_left(self):
        print("Steering left...")

    def steer_right(self):
        print("Steering right...")

    # ----- Actions -----
    def avoid_obstacle(self):
        if self.obstacles:
            print("Obstacle detected! Steering right and braking.")
            self.steer_right()
            self.brake()
            self.obstacles = False

    def check_traffic_light(self):
        if self.traffic_light == "Red":
            print("Red light! Stopping car.")
            self.stop()
        elif self.traffic_light == "Yellow":
            print("Yellow light! Slowing down.")
            self.brake()
        elif self.traffic_light == "Green":
            print("Green light! Moving forward.")
            self.accelerate()

    def drive(self):
        print(f"Starting from {self.location}, heading towards {self.destination}")
        self.check_traffic_light()
        self.avoid_obstacle()
        print(f"Driving at {self.speed} km/h...\n")

    # ----- Sensors -----
    def update_environment(self, traffic_light=None, obstacles=None):
        if traffic_light:
            self.traffic_light = traffic_light
        if obstacles is not None:
            self.obstacles = obstacles

    # ----- Status -----
    def print_status(self):
        print(f"Location: {self.location}, Destination: {self.destination}, "
              f"Speed: {self.speed}, Traffic Light: {self.traffic_light}, Obstacles: {self.obstacles}")
```
### Usage: 

```
car = SelfDrivingCarAgent()
car.print_status()

car.update_environment(traffic_light="Green")
car.drive()

car.update_environment(traffic_light="Red")
car.drive()

car.update_environment(obstacles=True)
car.drive()

```
### Output:

<img width="1076" height="404" alt="image" src="https://github.com/user-attachments/assets/bad99516-1072-4caf-b497-12739cf1c3a7" />


### Result:

The program has been successfully implemented and performs the intended tasks as designed.
