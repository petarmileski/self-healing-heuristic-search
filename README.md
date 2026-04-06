To reproduce all results reported in the paper, run:
python experiments.py

This script automatically:

launches the coordinator
spawns the required number of workers per experiment
injects predefined crash probabilities
collects runtime, memory, and performance metrics
saves results in JSON format


System components

coordinator.py
Runs the central task coordinator. It can be executed manually, but it will remain idle until workers connect and tasks are provided via the experiment runner.

worker.py
Runs a single worker process. If executed manually, it will start only one worker instance and connect to the coordinator.

experiments.py
Main entry point for all experiments. This is the only file required to reproduce results.

tasks.py – Implementation of the A* search algorithm and heuristics (Manhattan distance and misplaced tiles) used for all experiments

common.py – Shared utilities for message passing, heartbeat timing, and communication protocol between coordinator and workers


Note on worker setup

Earlier development versions used multiple individual worker scripts (e.g., worker1.py, worker2.py, …, worker20.py) for manual testing.
This is no longer needed.

The current implementation dynamically spawns workers using a loop inside experiments.py, making the system fully configurable and scalable.


Output

All experimental results are saved in the results_complete/ directory, including:

raw run logs
aggregated statistics
JSON summaries for analysis


