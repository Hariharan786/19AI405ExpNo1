<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: Hariharan Ganesh</h3>
<h3>Register Number: 212225040111</h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>
<h3>Program</h3>

```
import random

class HealthAgent:
    def __init__(self):
        self.current_room = "Ward 1"
        self.score = 0

    def take_action(self, hospital_env):
        current_temp = hospital_env[self.current_room]["temp"]
        
        if current_temp > 98.5:
            print(f"Patient in {self.current_room} has a fever ({current_temp:.1f}°F). Administering medication.")
            self.score += 10
            hospital_env[self.current_room]["temp"] = 98.5 
        else:
            print(f"Patient in {self.current_room} is healthy ({current_temp:.1f}°F). No action needed.")
            
        if self.current_room == "Ward 1":
            self.current_room = "Ward 2"
        else:
            self.current_room = "Ward 1"
            
        self.score -= 1
        print(f"Agent navigated to {self.current_room}. Current Score: {self.score}")

def main():
    hospital = {
        "Ward 1": {"temp": random.uniform(97.0, 102.0)},
        "Ward 2": {"temp": random.uniform(97.0, 102.0)}
    }
    
    nurse_bot = HealthAgent()
    
    print("--- Initiating Healthcare Simulation ---")
    
    for cycle in range(5):
        print(f"\n--- Cycle {cycle + 1} ---")
        nurse_bot.take_action(hospital)
        
        random_ward = random.choice(["Ward 1", "Ward 2"])
        hospital[random_ward]["temp"] = random.uniform(99.0, 103.0)

    print("\n--- Simulation Concluded ---")

if __name__ == "__main__":
    main()

```
<h3>Output</h3>

<img width="918" height="495" alt="image" src="https://github.com/user-attachments/assets/4a45b481-4166-4bc3-95d8-bf764cffddaf" />

<h3>Result</h3>

The PEAS description for the given AI problem is finded and successfully developed an AI agent.
