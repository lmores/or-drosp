# The Dynamic Remote Operations Scheduling Problem (DROSP)

This repository contains the data for the instances mentioned in the article _"A multi-level rescheduling approach for a dynamic remote operations scheduling problem"_ by A. Castelletti, L. Moreschini[^1], M. Corvaglia and R. Mansini published on the Internation Journal of Production Research, [https://doi.org/10.1080/00207543.2024.2408438](https://doi.org/10.1080/00207543.2024.2408438).


## Data format

Each directory inside the [instances](instances/) folder contains the data for one of the 30 instances mentioned in the above research article.
Each directory contains the following files:

```text
- instances/
    - instanceX/
        - instanceX.json
        - instanceX_u1.json
        - instanceX_u2.json
        - instanceX_u3.json
        - instanceX_u4.json
```

Each file named `instanceX.json` contains the data of the tasks that must be scheduled since the beginning.
This file contains a JSON object with the following properties:

  * `name`: a string, the unique identifier of the instance,
  * `workers`: an object that maps the name of each worker to an object of type `Worker` (see below),
  * `project_tasks`: an object that maps the name of each project task to an object of type `ProjectTask` (see below),
  * `projects`: an object that maps the name of each project to an object of type `Project` (see below),
  * `meeting_tasks`: an object that maps the name of each meeting task to an object of type `MeetingTask` (see below),
  * `trainings`: an object that maps the name of each training to an object of type `Training` (see below).

Files `instanceX_u1.json`, `instanceX_u2.json`, `instanceX_u3.json`, and `instanceX_u4.json` contain the data of the new tasks that must be included in a schedule during the first, second, third, and fourth update, respectively.
These files contain a JSON object with the following properties:

  * `name`: a string, the unique identifier of the update,
  * `new_project_tasks`: an object that maps the name of each incoming project task to an object of type `ProjectTask` (see below),
  * `new_projects`: an object that maps the name of each incoming project to an object of type `Project` (see below),
  * `new_meeting_tasks`: an object that maps the name of each incoming meeting task to an object of type `MeetingTask` (see below),
  * `new_trainings`: an object that maps the name of each incoming training to an object of type `Training` (see below).

Each object of type `Worker` has the following properties:

  * `name`: a string, the unique identifier of the worker,
  * `allowed_projects`: a list of string, the names of the projects that the worker can execute.

Each object of type `Project task` has the following properties:

  * `name`: a string, the unique identifier of the task,
  * `release_time`: an integer, the minimum start time for the task,
  * `deadline_time`: an integer, the maximum completion time for the task,
  * `processing_time`: an integer, the number of time slots needed to execute the task,
  * `requirements`: a list of strings, the names of tasks that must be completed before the current one may begin,
  * `project`: a string, the name of the project this task belongs to.

Each object of type `Meeting task` has the following properties:

  * `name`: a string, the unique identifier of the task,
  * `release_time`: an integer, the minimum start time for the task,
  * `deadline_time`: an integer, the maximum completion time for the task,
  * `processing_time`: an integer, the number of time slots needed to execute the task,
  * `requirements`: a list of strings, the names of tasks that must be completed before the current one may begin,
  * `worker_names`: a list of strings, the names of the workers that must take part in the meeting.

Each object of type `Project` has the following properties:

  * `name`: a string, the unique identifier of the project,
  * `task_names`: a list of strings, the names of the tasks that belong to this project,
  * `allowed_workers`: a list of strings, the names of the workers that may execute the tasks of this project.

Each object of type `Training` has the following properties:

  * `name`: a string, the unique identifier of the training,
  * `worker_name`: a string, the name of worker that must be trained,
  * `task_pool`: a list of strings, the names of the tasks that may be chosen to train the worker,
  * `min_duration`: an integer, the minimum total duration of the tasks chosen to carry out the training.


## How to cite

```bibtex
@article{
    TODO
}
```


  [^1]: Corresponding author, contact him at <lorenzo.moreschini@unibs.it>.
