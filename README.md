# Task Scheduler with Max Heap Priority Queue

## Overview

This project implements a daily task scheduler using a custom **Max Heap** to prioritize tasks. The scheduler efficiently manages tasks based on their dependencies, deadlines, and priority scores. It includes functionality for fixed-start tasks, efficiency metrics, and performance scaling with large inputs.

---

## Features

### 1. **Max Heap Implementation**
- A custom `MaxHeap` class is built from scratch.
- Maintains the highest-priority task at the root.
- Supports insertion (`heappush`) and removal (`heappop`) while ensuring the heap property.

### 2. **Task Management**
- Each task has attributes such as:
  - Duration
  - Deadline
  - Dependencies
  - Fixed start time
  - Dynamic priority score
- Tasks are prioritized based on their proximity to deadlines, dependency counts, and constraints.

### 3. **Task Scheduler**
- Schedules tasks using two priority queues:
  - General tasks.
  - Fixed-start tasks.
- Supports two modes:
  - **Run Scheduler:** Completes all tasks until no further scheduling is possible.
  - **24-Hour Scheduler:** Limits scheduling to a 24-hour period to simulate daily efficiency.

### 4. **Efficiency Metrics**
- **Task Completion Rate**: Percentage of tasks completed.
- **Time Utilization**: Ratio of productive time to total scheduling time.
- **Total Utility**: Net utility of completed tasks, accounting for priorities and missed opportunities.

### 5. **Scalability**
- Performance tested with increasing task counts.
- Plots average scheduling time against task count to evaluate efficiency.

### 6. **Test Cases**
- Comprehensive tests covering:
  - Empty heap and single-element operations.
  - Insertion and removal of multiple elements.
  - Duplicate values and extreme inputs (e.g., ±infinity).
  - Order consistency for shuffled inputs.

---

## Usage

### 1. **Running the Scheduler**
- Initialize tasks with attributes such as duration, deadline, and dependencies.
- Run either:
  - **`runTaskScheduler()`**: Completes all tasks with no time limit.
  - **`run24HoursTaskScheduler()`**: Completes tasks within a 24-hour period.

```python
scheduler = TaskScheduler(tasks)
scheduler.runTaskScheduler(startingTimeMins=6*60)  # Start at 6:00 AM
```

### 2. **Generating Tasks**
- Randomly generate tasks for scalability tests.

```python
tasks = generate_tasks(20)  # Generate 20 tasks with random attributes
```

### 3. **Analyzing Efficiency**
- Calculate and display task scheduler metrics.

```python
metrics = calculate_efficiency_metrics(tasks, startingTimeMins=0)
for metric, value in metrics.items():
    print(f"{metric}: {value:.2f}")
```

### 4. **Scalability Testing**
- Evaluate average scheduling time against task count.

```python
plt.plot(xAxis, averageTimes)
plt.xlabel('Number of Tasks')
plt.ylabel('Average Time (s)')
plt.title('Average Time vs Number of Tasks')
plt.show()
```

---

## Example Task Attributes

```python
Task(
    id=1,
    description="Attend Lecture",
    durationMins=90,
    deadlineTimeConstraintMins=600,  # Deadline at 10:00 AM
    dependencies=[2, 3],  # Must complete tasks 2 and 3 first
    fixedStartTime=True  # Fixed start time at deadline
)
```

---

## Results

### Test Cases:
- Verified heap operations (push, pop) maintain correct properties.
- Confirmed scheduler handles dependencies, deadlines, and fixed-start tasks.
- Order consistency validated for shuffled inputs.

### Efficiency Metrics:
- Task completion rate: Percentage of tasks completed within the schedule.
- Time utilization: Fraction of productive time.
- Total utility: Sum of priority scores for completed tasks.

### Performance:
- Average scheduling time scales linearly with task count, demonstrating efficiency.
- Scheduler efficiently prioritizes tasks while respecting constraints.

---

## Tools and Libraries
- **Python Libraries**: `math`, `random`, `matplotlib`, `time`.
- **Data Structures**:
  - Max Heap for priority queues.
  - Dynamic programming for dependency resolution.

---

## Future Enhancements
- Add support for recurring tasks.
- Optimize heap operations for larger task sets.
- Visualize task schedules in Gantt charts for better insights.
