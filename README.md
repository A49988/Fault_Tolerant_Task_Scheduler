# Fault_Tolerant_Task_Scheduler
Many systems need to perform periodic tasks, such as generating reports, compressing old files, verifying data integrity, or cleaning up temporary directories. When a single machine suffices, tools like `cron` solve the problem. However, a single machine limits the number of tasks that can be executed; furthermore, if it fails, no tasks run. Distributing `cron` across multiple nodes overcomes these limitations but introduces two new challenges:

- if all nodes trigger the execution of tasks, each task runs N times;
- if only one node triggers the execution, and that node fails, the tasks cease to run.
The objective of this project is to build a distributed scheduler in which only one node (the leader) triggers the tasks. Execution is carried out by a scalable set of workers, and the system continues to function correctly even in the event of a failure involving a scheduler or a worker.

The project is organized into four incremental phases. The Spread middleware will be used for leader election and message broadcasting among the group of schedulers. The Gluster File System will be used in the final phase to facilitate file sharing between VMs.
