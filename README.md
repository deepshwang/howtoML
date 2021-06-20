# How to manage large-scale / multiple ML experiments

## Why this is a MUST

* A good theory itself cannot comprise a good network: EXPERIMENTS over EXPERIMENTS
* A well-organized experiments will
  * save you so much time
  * help you find better network architecture
  * Easier to write papers later on
* Remind yourself: There must be countless experiments behind works from other papers that looks like it worked well by the theory itself.

(To-Do): What I've learned & will implement
(Ing): What I am already using

## What to set-up before starting experiments of a project

1. Global set-up of environments using docker images & docker hub (Ing)
 * When conducting multiple experiment sessions with multiple machines in parallel, it's tedious to conduct environment setting for every machine.
 * Also, there are some environments that's hard to configure with conda only => Docker image enables to store separate environments for different projects.
 * Here's how to set up & manage your docker environment in cloud.   

2. Data visualization tools (Ing)
 * It's important to see how data looks like in different circumstances.

3. Training progress visualization tools (Ing, but not good enough)

## How to organize your experiment procedures

```
| .gitignore
| main.py
**| experiments\
  | 210601\
    | config_training.yaml
    | state_dict\
      | checkpoint_best.pt
      | checkpoint_e_0.pt
      | checkpoint_e_50.pt
      |...
    | README.md**
  ...
| data\
  | DataA.py
  | DataB.py

| models\
  | modules.py
  | netA.py
  | netB.py
  ...

```

1. Store configuration for every experiment as a single configuration file (yaml / json)
* For training configuration, let's migrate from argparse -> yaml 
