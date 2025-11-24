# Report on Experiments with Dropout, Normalization, and Additional Layers

## Objective
This week focused on expanding previous experiments with more hyperparameters and architectural components. According to the assignment, dropout, normalization layers, convolutional/pooling layers, and logging with MLflow were to be added. In addition, the emphasis was on the scientific process: formulating a hypothesis, setting up an experiment, executing it, and reflecting on the results.

## Hypothesis
My expectation was that dropout would reduce overfitting and improve generalization without significantly increasing training time. I also expected that normalization (e.g., batch normalization) would lead to more stable training and faster convergence. Furthermore, I anticipated that convolutional layers would learn patterns more efficiently than dense layers alone.

## Experiments
Due to circumstances (SURF server unavailable), I was only able to perform limited experiments. I mainly focused on the effect of dropout in the dense layers

- Model without dropout (baseline): after 3 epochs, accuracy of ~87.8%.  
- Model with dropout (p=0.5 after two dense layers): after 3 epochs, accuracy of ~84.1%.  
- Training times remained approximately the same (~5:47 minutes).

I also briefly explored MLflow logging: runs are recorded, including accuracy and loss, though it takes time to become familiar with it. Therefore, I still record configurations and accuracy manually as well.

## Analysis
- Dropout did not ** performance in this configuration; accuracy was slightly lower. Possibly, the dataset is large enough and the model small enough that overfitting is not yet a major issue.  
- Training duration hardly changed with the addition of dropout, contrary to my expectation that it might speed up.  
- This highlights that the choice of hyperparameters is always dataset- and model-dependent. Dropout is not a guaranteed improvement, especially for relatively simple models.  

## Reflection
Due to technical limitations, I was only able to complete part of the assignment. Nevertheless, I learned that:
- It is important to test one variable at a time so results can be interpreted clearly.  

## Conclusion
Due to the server issue, I was only able to work on this assignment to a limited extent.
