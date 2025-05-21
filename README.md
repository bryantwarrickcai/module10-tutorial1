# Module 10
## 1.2 Understanding how it works
![1.2 Understanding how it works](1-2.png)

The program first sets up a task queue with a sender (spawner, that creates new tasks) and a receiver (executor, that runs tasks). The next lines spawn an asynchronous task that prints "Bryant's Computer: howdy!", then waits 2 seconds using a custom future (called `TimerFuture`), and finally prints "Bryant's Computer: done!". This future is boxed and sent into the task queue via `Spawner`. Before running the executor, the print statement prints "Bryant's Computer: hey hey" immediately into the console before the other two messages (this is on the main thread still running synchronously).

After that, the spawner is dropped, telling the executor that there are no more tasks to be sent. This allows the executor to eventually exit the loop when all tasks are done. Finally, the line `executor.run();` will start the main task execution loop. It takes the tasks from the queue and runs them as part of their logic.
