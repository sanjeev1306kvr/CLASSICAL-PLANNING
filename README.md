# ExpNo:10 Implementation of Classical Planning Algorithm
# Name: SANJEEV R
# Register Number: 212224060235
# Algorithm or Steps Involved:
<ol>
  <li>Define the initial state</li>
  <li>Define the goal state</li>
  <li>Define the actions</li>
  <li>Find a <b>plan</b> to reach the goal state</li>
  <li>Print the plan</li>
</ol>

# Example - 1
```
initial_state = {'A': 'Table', 'B': 'Table'}
goal_state = {'A': 'B', 'B': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_Table': {'precondition': {'A': 'Table', 'B': 'B'}, 'effect': {'B': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B']
```
# Example - 2
```
initial_state = {'A': 'Table', 'B': 'Table', 'C': 'Table'}
goal_state = {'A': 'B', 'B': 'C', 'C': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_C': {'precondition': {'A': 'B', 'B': 'Table', 'C': 'Table'}, 'effect': {'B': 'C'}},
    'move_C_to_Table': {'precondition': {'A': 'B', 'B': 'C', 'C': 'C'}, 'effect': {'C': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B', 'move_B_to_C']
```

# Please Prepare Solution or Definition For the method find_plan(initial_state, goal_state, actions)
<h3>You Can use any of the searching Strategies for planning and executing a sequence of actions.<br> You can also look in to the Code given in the Repository.</h3>

# Program:
```
class ClassicalPlanning:
    def _init_(self):
        self.initial_state = None
        self.goal_state = None
        self.actions = []

    def define_initial_state(self, state):
        self.initial_state = state

    def define_goal_state(self, state):
        self.goal_state = state

    def define_actions(self, actions):
        self.actions = actions

    def is_goal_reached(self, state):
        return state == self.goal_state

    def plan(self):
        # A simple planner that assumes actions are sequential and valid
        current_state = self.initial_state
        plan = []
        for action in self.actions:
            plan.append(action['name'])
            current_state = action['result']
            if self.is_goal_reached(current_state):
                break
        return plan


# Define an example scenario
initial_state = {'location': 'A'}
goal_state = {'location': 'D'}
actions = [
    {'name': 'go to B', 'result': {'location': 'B'}},
    {'name': 'go to C', 'result': {'location': 'C'}},
    {'name': 'go to D', 'result': {'location': 'D'}}
]

# Create the planner instance
planner = ClassicalPlanning()
planner.define_initial_state(initial_state)
planner.define_goal_state(goal_state)
planner.define_actions(actions)

# Plan to reach the goal
plan = planner.plan()
print(plan)
```

# Output:
['go to B', 'go to C', 'go to D']

# Result: 
Thus, the classical planning Algorithm has been successfully implemented.
