# How to manage large-scale / multiple ML experiments

## 0. Why this is a MUST

* A good theory itself cannot comprise a good network: EXPERIMENTS over EXPERIMENTS
* A well-organized experiments will
  * save you so much time
  * help you find better network architecture
  * Easier to write papers later on
* Remind yourself: There must be countless experiments behind works from other papers that looks like it worked well by the theory itself.

(To-Do): What I've learned & will implement
(Ing): What I am already using

## 1. What to set-up before starting experiments of a project

### A. Global set-up of environments using docker images & docker cloud(Ing)
 * When conducting multiple experiment sessions with multiple machines in parallel, it's tedious to conduct environment setting for every machine.
 * Also, there are some environments that's hard to configure with conda only => Docker image enables to store separate environments for different projects.
 * **Docker commit your environemnt to your docker respository so that you can pull it to any other machine for use!**
 * [My tips on dockers](https://docs.google.com/document/d/1-L2QjWVNap4urUJ62t9xC-BZTUi0W2m2DUha_pfuW9s/edit?usp=sharing)    

### B. Data visualization tools (Ing)
 * It's important to see how data looks like in different circumstances.

### C. Training progress visualization tools (Ing, but not good enough)
 * For now, I am using Visdom - A simple drawing tool
 * However, it's **not good for saving & comparing results from different experiments**
 * There are some tools, and I'll select one of them to use

   i. [Guild AI](https://my.guild.ai/)
   ii. [Weights & Biases](https://wandb.ai/site)

### D. Write experiment diary (Ing, but not good enough)
 * For now, I've been using google doc powerpoint
 * However, it's not good enough to organize different ideas / data type
 * MIGRATE TO: Notion [example: ECL-Transformer](https://www.notion.so/ECL-Transformer-Logs-3dc12843976d4af38522997be8935ca3)

## 2. How to organize your experiment procedures

```
| .gitignore
| main.py
  | experiments\
  | 210601\
    | config_training.yaml
    | log.txt
    | state_dict\
      | checkpoint_best.pt
      | checkpoint_e_0.pt
      | checkpoint_e_50.pt
      |...
    | README.md
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

### Store configuration for every experiment as a single configuration file (yaml / json)
* For training configuration, let's migrate from argparse -> yaml 

### Git commit different implementation in different branch

