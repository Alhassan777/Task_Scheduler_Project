# Task Scheduler

## Overview

The Task Scheduler is a Python-based system designed to manage tasks with varying priorities, dependencies, and time constraints. The scheduler can handle complex requirements like task dependencies, deadlines, time sensitivity, and different task types, making it ideal for organizing tasks in a priority-based, dynamic environment.

## Key Features

- **Priority Management**: Implements a custom priority queue using a MaxHeap to efficiently manage and retrieve the highest-priority tasks.
- **Task Dependencies**: Uses Depth-First Search (DFS) to identify and handle task dependencies and detect any cycles within the dependency graph.
- **Time Sensitivity and Deadlines**: Supports tasks with specific time constraints, allowing tasks to be categorized based on urgency.
- **Task Types**: Handles different types of tasks (e.g., work, self-care, meetings) to provide flexibility in scheduling.
- **Robust Data Structure Choice**: Optimizes performance by choosing suitable data structures like heaps, arrays, and linked lists for different scheduling scenarios.
## Usage

1. **Define Tasks**: Create task instances by specifying their attributes such as ID, description, duration, dependencies, deadline, time sensitivity, and type.

   ```python
   task_1 = Task(
       id=1,
       description='Complete project report',
       duration=120,
       dependencies=[],
       deadline="12:00",  # Must be completed by 12:00 PM
       time_sensitivity=TimeSensitivity.HIGH_PRIORITY,
       task_type=TaskType.WORK
   )

   task_2 = Task(
       id=2,
       description='Eat a healthy breakfast.',
       duration=40,
       dependencies=[0],
       deadline="09:30",  # Must be completed by 9:30 AM
       time_sensitivity=TimeSensitivity.FREE_FOR_ALL,
       task_type=TaskType.SELF_CARE
   )
2. **Initialize Scheduler**: Instantiate the `TaskScheduler` with a list of tasks.

   ```python
   scheduler = TaskScheduler([task_1, task_2])
3. **Run the Scheduler**: Execute the scheduling algorithm to arrange tasks based on priority, dependencies, and deadlines.

   ```python
   scheduler.run_scheduler()

## Task Details

Each `Task` has the following attributes:

- **`ID`**: A unique identifier for each task.
- **`Description`**: A brief description of the task.
- **`Duration`**: Time (in minutes) required to complete the task.
- **`Dependencies`**: List of task IDs that must be completed before this task.
- **`Deadline`**: The latest time by which the task should be completed.
- **`Time Sensitivity`**: Priority level of the task, e.g., high priority or free for all.
- **`Task Type`**: Categorizes the task (academics, work, self-care (mental, emotional, physical), chores, recreation).

## Core Components

- **MaxHeap**: A custom implementation for managing tasks based on priority.
- **Depth-First Search (DFS)**: Used to detect cycles in task dependencies.
- **Priority Function**: Calculates task priority based on factors like time sensitivity, deadline, and dependencies.
