Last week, you have been experimenting with the interaction of hyperparameters.
You made visualisations to show how they impacted each other.
This week, you will extend the number of hyperparameters and architectures you can experiment with.

# 1. Study more layers to add
Study the pytorch documentation for:
- Dropout https://pytorch.org/docs/stable/generated/torch.nn.Dropout.html
- normalization layers https://pytorch.org/docs/stable/nn.html#normalization-layers

# 2. Add dropout and normalization layers to your model
Experiment with adding dropout and normalization layers to your model. Some rough guidelines where to add them relative to Linear or Conv2d layers:
- Dropout: after Linear or Conv2d layers. Often added after the last Linear layer *before* the output layer, but could occur more often.
- Normalization layers: right after (blocks of) Linear or Conv2d layers, but before activation functions.

Default is 5:46, 87,8%
100%|██████████| 937/937 [01:47<00:00,  8.70it/s]
2025-09-18 15:35:05.641 | INFO     | mltrainer.trainer:report:209 - Epoch 0 train 0.7262 test 0.5461 metric ['0.7929']
100%|██████████| 937/937 [01:47<00:00,  8.71it/s]
2025-09-18 15:37:00.550 | INFO     | mltrainer.trainer:report:209 - Epoch 1 train 0.4305 test 0.4013 metric ['0.8554']
100%|██████████| 937/937 [01:48<00:00,  8.62it/s]
2025-09-18 15:38:56.626 | INFO     | mltrainer.trainer:report:209 - Epoch 2 train 0.3435 test 0.3324 metric ['0.8781']
100%|██████████| 3/3 [05:46<00:00, 115.56s/it]

  Add dropout in de dense layers. I expect it to run faster with same accuray 

          self.dense = nn.Sequential(
            nn.Flatten(),
            nn.Linear(filters, units1),
            nn.ReLU(),
            nn.Dropout(p=0.5),        # toevoeging KJ
            nn.Linear(units1, units2),
            nn.ReLU(),
            nn.Dropout(p=0.5),        #toevoeging kj
            nn.Linear(units2, 10)

  dropout added = time trainer.loop() = 5:47 and 0.8411% is max
  100%|██████████| 937/937 [01:46<00:00,  8.77it/s]
2025-09-18 15:25:15.489 | INFO     | mltrainer.trainer:report:209 - Epoch 0 train 1.0034 test 0.5529 metric ['0.7874']
100%|██████████| 937/937 [01:47<00:00,  8.73it/s]
2025-09-18 15:27:11.975 | INFO     | mltrainer.trainer:report:209 - Epoch 1 train 0.5704 test 0.4409 metric ['0.8391']
100%|██████████| 937/937 [01:47<00:00,  8.75it/s]
2025-09-18 15:29:07.174 | INFO     | mltrainer.trainer:report:209 - Epoch 2 train 0.4733 test 0.4218 metric ['0.8411']
100%|██████████| 3/3 [05:47<00:00, 115.96s/it]

# 3. Use logging
- set up logging with MLflow, and make sure the hyperparameters you are using are logged.
- get comfortable with using MLflow to visualize your results, it has a pretty powerful dashboard.

# 4. Adding convolutional and pooling layers
This lesson, we have added some new types of layers: convolutional and pooling layers.
Experiment with adding these new layers.

Also, have a look at the `ModuleList`: https://pytorch.org/docs/stable/generated/torch.nn.ModuleList.html#modulelist
This makes it much easier to use the number of layers as a hyperparameter.
You can create a list of layers from a config, and then use that list to create your model.
Instead of just adding a single layer by hand, you could also add a block of layers as a unit (eg a Conv2d layer, followed by a ReLU layer, followed by a BatchNorm2d layer, followed by a MaxPool2d layer) and repeat that in a loop, adding it to the `ModuleList`.

# 5. Reflect
Doing a master means you don't just start engineering a pipeline, but you need to reflect. Why do you see the results you see? What does this mean, considering the theory? Write down lessons learned and reflections, based on experimental results. This is the `science` part of `data science`.

You follow this cycle:
- make a hypothesis
- design an experiment
- run the experiment
- analyze the results and draw conclusions
- repeat

To keep track of this process, it is useful to keep a journal. While you could use anything to do so, a nice command line tool is [jrnl](https://jrnl.sh/en/stable/). This gives you the advantage of staying in the terminal, just type down your ideas during the process, and you can always look back at what you have done.
Try to first formulate a hypothesis, and then design an experiment to test it. This will help you to stay focused on the goal, and not get lost in the data.

Important: the report you write is NOT the same as your journal! The journal will help you to keep track of your process, and later write down a reflection on what you have done where you draw conclusion, reflecting back on the theory.

# 6. Make a short report
Make a short 1 a4 page report of your findings.
pay attention to:
- what was your hypothesis about interaction between hyperparameters?
- what did you find?
- visualise your results about the relationship between hyperparameters.
