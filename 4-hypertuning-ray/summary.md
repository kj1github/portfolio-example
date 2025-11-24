# Summary Week 4  
Hypertuning Fashion

## 1. Introduction
In the hypertuning lessons, we focused on the concept of hypertuning. In the example, two parameters were tuned (hidden size and number of layers) on the gestures dataset.  
This notebook was adapted to the Fashion dataset, where we use a CNN model to predict the 10 classes.  
Two parameters were tuned: the **learning rate** and the **number of filters**.  
Due to performance limitations of the SURF environment, the parameters were kept relatively small.

---

## 2. Hypothesis
I formulated a simple hypothesis:  
A higher number of filters leads to higher accuracy but also to longer training times.

---

## 3. Experiment
Experiments were conducted using four hypertuning methods (**random search**, **bayes**, **hyperband**, and **hyperopt**) for 10 epochs each.  
The configuration was the same for all hypertuners:
- `"filters": tune.randint(2,16)`
- `"units1": 128`
- `"units2": 64`
- `"lr": tune.loguniform(1e-4, 3e-3)`

### Random Search
(see table and plot below)

| Trial name              | Status      | Loc                  | Filters | LR          | Iter | Total time (s) | Valid loss | Train loss | Accuracy |
|--------------------------|-------------|----------------------|----------|--------------|------|----------------|-------------|-------------|-----------|
| tune_model_79a39_00000  | TERMINATED  | 192.168.3.171:62204 | 4        | 0.000309012  | 10   | 107.409        | 0.727666    | 0.731288    | 0.720453  |
| tune_model_79a39_00001  | TERMINATED  | 192.168.3.171:62203 | 14       | 0.000548393  | 10   | 245.611        | 0.384764    | 0.354075    | 0.856971  |
| ... *(remaining trials omitted for brevity)* ... |

<img width="927" height="405" alt="plot accuracy" src="https://github.com/user-attachments/assets/c5e59bbd-6610-43bf-b322-87cec5aa5807" />

---

### Bayes
(see table above)

---

### Hyperband
(see table above)

---

### Hyperopt
(see table above)

<img width="458" height="413" alt="plot_times" src="https://github.com/user-attachments/assets/dfa56dcf-e7fe-44be-8038-c8c1c63a9faf" />

| Method     | Epochs | Tune dir                                                    | Filters | Units1 | Units2 | LR       | Accuracy |
|-------------|---------|------------------------------------------------------------|----------|--------|--------|-----------|-----------|
| random      | 10      | /home/kkisteman/MADS-MachineLearning-course/no...         | 12.000000 | 128    | 64     | 0.001229  | 0.881010  |
| bayes       | 10      | /home/kkisteman/MADS-MachineLearning-course/no...         | 12.247915 | 128    | 64     | 0.001836  | 0.871294  |
| hyperband   | 10      | /home/kkisteman/MADS-MachineLearning-course/no...         | 14.000000 | 128    | 64     | 0.002596  | 0.875601  |
| hyperopt    | 10      | /home/kkisteman/MADS-MachineLearning-course/no...         | 15.000000 | 128    | 64     | 0.001909  | 0.884615  |

---

## 4. Analysis / Reflection
All hypertuning methods achieved roughly similar accuracies. This suggests that the different methods found similar hyperparameter combinations.  
Among them, **Hyperopt** performed best.  
In terms of training time, **Bayes** and **Random Search** took the longest, while **Hype**
