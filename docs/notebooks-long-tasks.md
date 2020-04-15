# Running Long Tasks in Notebooks

!!! tldr
    - Notebooks are a great tool, but they're not adequate for long-running tasks.
    - The problem is that only one cell can run at a time, which makes changes cumbersome when the notebook is already running.
    - The solution is to turn your notebook into a Python file using Jupytext so you can run it in the background.

Notebooks make it comfortable to quickly implement new research ideas. 
You try things out with a toy dataset, and after a few iterations, you're reasonably sure that you got things right. 

Next step: trying it out on a more realistic dataset! This usually means having to wait for some time.
In theory, nothing stops you from simply executing the notebook and letting it run for a few hours.
 
In practice, this is generally a ***bad idea***.

We will see why, and how to solve potential problems by integrating new tools to your workflow.

Notebooks hinder your flow
---

Let's assume you only need 10 minutes to run your notebook. 
Note that you should always run it from beginning to end, after having restarted the runtime, to avoid problems with [stale states](notebook-pitfalls.md#error-prone-execution-flow)! 

Now that your notebook is running, what do you do? The problem is that you can only run *one cell at a time*.
As long as it is running, you should be careful what you.

One option is to **keep making changes** to other cells, cleaning up your code or adding comments. 
The problem is that it now becomes unclear what was the state when you started the task. 
If it crashes mid-way through, it will be painful to debug, as you won't be sure which changes were made before or after it started.
Even if the task doesn't crash, you can't run any other cell in the meantime, losing one of the main selling point of notebooks: instant feedback.

Another option is to immediately **duplicate the notebook**. This is a common pattern among Kaggle participants.
The advantage is that you keep a clear snapshot of the state in which the task started. 
The problem is that you end up with multiple different "branches" of your work, that quickly get hard to reconcile.

Finally, you can also do **something else entirely**: work on another notebook, read Reddit or go grab coffee. 
But the problem is that you **_are forced_** to do these things, because of your workflow - this is bad! your workflow shouldn't force you to context-switch if you don't want to.

Connection issues
---

Another problem is that notebooks are not reliable enough to run for hours. Crucially, they are not able to recover if you lose connection to the kernel.

You accidentally close your laptop? You lose connectivity for a few seconds? Too bad! You won't be able to recover the output of your task.

If you are using [Google Colab](https://colab.research.google.com/), another risk is that your runtime gets killed because of inactivity, or just because of lack of capacity.

Sure, you can mitigate this problem by using some form of checkpointing, but this is a band-aid. Couldn't notebooks handle this better? I have been keeping an eye on [two](https://github.com/jupyter/notebook/issues/1150) [separate](https://github.com/jupyterlab/jupyterlab/issues/2833) GitHub issues tracking this problem for a long time, and they are still open to this day.

Git and Jupytext to the rescue
---

So, what's the solution? It depends how long your task takes. 

For notebooks that run **for a few minutes**, I would recommend adopting a rigorous **git workflow**: commit your code and parameters before each run. This allows you to keep making minor changes to your code while keeping a snapshot of the starting state. You still run into the problems mentioned above: you can't run other cells in the meantime, and you'll lose progress if you get disconnected. But for a few minutes, this is usually fine.

For tasks that will run **for hours**, it is simply not reasonable to keep a browser tab opened for that long. The solution in that case is to turn your notebook into a **Python file**. One way to do this is to manually extract each cell, in order to turn your work into a proper Python module. This is usually a good idea when you have high confidence that things work as expected, and you move from an experimental mindset to a production mindset.

But this is a lot of work! Couldn't that be automated? Yes it can!

The solution is called [Jupytext](https://github.com/mwouts/jupytext). Jupytext takes a Python notebook as input, and turns it into a plain Python file. This gives you the best of both worlds! You can now easily run your experiment in the background, or on another machine, in a "fire and forget" way. You can easily run multiple instances, for example to perform some basic hyperparameter search or check variance across multiple seeds. And you can start your task using robust Unix tools such as `screen` and `tmux` to ensure it will run to completion. 

Other notebook pitfalls
---

Notebooks are an amazing tool, but they require some careful considerations before you integrate them into your workflow. You can read more on this topic in the article [Notebook Pitfalls](notebook-pitfalls.md). 