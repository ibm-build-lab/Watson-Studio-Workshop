# Using the Progress Listeners with CPLEX Optimizer
​
This tutorial includes everything you need to set up decision optimization engines, build a mathematical programming model, and then use the progress listeners to monitor progress, capture intermediate solutions, and stop the solve.
​
## Step 1: Download the library
​
First, we need to install the DOcplex library which is necessary to formulate the optimization models. Install it from PyPI using pip.
​
​
```
pip install docplex
```
​
## Step 2: Set up the prescriptive model
The problem can be modeled by using the mathematical modeling portion of DOcplex. Here's how you can import the required class and define a placeholder model:
​
```
from docplex.mp.model import Model
​
def build_hearts():
    m = Model("Hearts")
    # Add variables, constraints and objective function here
    # ...
    return m
```
​
## Step 3: Use the model to make decisions
Once your model is properly set up, you can use DOcplex to solve it:
​
```
m = build_hearts()
s = m.solve()
```
​
## Step 4: Display the solution
The solution to the problem can be displayed with a simple command:
​
```
m.print_solution()
```
​
## Step 5: Modify the model and resolve
The model can be modified and resolved to get a different solution. This process will depend on the specifics of the problem and the changes required. After making modifications, you can call m.solve() again.
​
# Using the progress listeners to monitor CPLEX progress
​
## Step 1: Set up the environment
You need the IBM Decision Optimization CPLEX Modeling for Python to use progress listeners. You can install it via pip:
​
```
pip install docplex
```
​
## Step 2: Monitoring CPLEX progress
​
### An introduction to progress listeners
Progress listeners are objects, sub-classes of the docplex.mp.progress.ProgressListener class. They allow monitoring of the CPLEX MIP search:
​
```
from docplex.mp.progress import *
```
​
### Monitoring MIP search progress
We can use the TextProgressListener to print a message on the STDOUT each time it is called:
​
```
m.add_progress_listener(TextProgressListener())
m.solve(clean_before_solve=True);
```
​
​
### Listener clocks
The ProgressClock enumerated type defines types of events to listen to:
​
```
for l, listener in enumerate(m.iter_progress_listeners(), start=1):
    print("listener #{0} has type '{1}', clock={2}".format(l, listener.__class__.__name__, listener.clock))
```
​
### Monitor progress: manage intermediate solutions
The SolutionRecorder class is used to manage intermediate solutions:
​
```
from docplex.mp.progress import SolutionRecorder
​
sol_recorder = SolutionRecorder()
m.clear_progress_listeners()
m.add_progress_listener(sol_recorder)
m.solve(clean_before_solve=True);
```
​
## Step 3: Aborting the search with a custom progress listener
Custom progress listeners can be created to abort the search under certain conditions:
​
```
from docplex.mp.progress import ProgressListener
​
class AutomaticAborter(ProgressListener):
    # code for the AutomaticAborter class
```
​
## Step 4: Produce advancement charts
​
### Using a custom progress listener
A custom progress listener can be used to print the gap and time:
```
class MipGapPrinter(ProgressListener):
    # code for the MipGapPrinter class
```
​
### Using matplotlib to plot a chart of gap vs. time
matplotlib can be used to create a chart of the gap versus time:
​
```
import matplotlib.pyplot as plt
​
class MipGapPlotter(ProgressListener):
    # code for the MipGapPlotter class
```
​
## Summary
You have learned how to set up and use the IBM Decision Optimization CPLEX Modeling for Python to formulate a Mathematical Programming model and track its progress. mode detailed document available (here)[https://github.com/IBMDecisionOptimization/DO-Samples/blob/watson_studio_cloud/jupyter/Watson%20Studio%20Public/Using%20the%20Progress%20Listeners%20with%20CPLEX%20Optimizer.ipynb]