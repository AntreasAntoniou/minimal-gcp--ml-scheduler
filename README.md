### Machine Learning Experiment Scheduler for GCP using WnB and Hydra


1. Get a target runner script, a list of experiment configs, and a list of hardware requirement configurations, i.e.
```python
exp_configs: List[Dict], resource_configs: List[Dict], runner_script: str = /target_codebase/runner.py
```
2. For each experiment config + resource config pair launch an instance that has the right requirements.
3. Pass to the instance during launch a startup script that runs the `runner_script`.
4. Monitor the experiments using the wandb package to ensure that any failed experiments are continued. A selected variable such as `epoch` will be used to ensure an experiment is completed.
5. Monitor the number of instances running at time, or perhaps just the total number of resources? It would be cool if we could track spending as well. Make sure it doesn't exceed some given threshold.
6. Map experiments to instances and ping instances every so often to make sure they are running. Can also be done via wandb by checking the `status` variable.


