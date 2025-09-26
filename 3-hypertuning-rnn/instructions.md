# Excercises

- try to improve the RNN model
- test different things. What works? What does not?
- experiment with either GRU or LSTM layers, create your own models. Have a look at `mltrainer.rnn_models` for inspiration.
- experiment with adding Conv1D layers. Think about the necessary input-output dimensions of your tensors before and after each layer.

You should be able to get above 90% accuracy with the dataset.
Create a report of 1 a4 about your experiments.



Can you make sense of the shape?
What does it mean that the shapes are sometimes (32, 27, 3), but a second time might look like (32, 30, 3)? In other words, the second (or first, if you insist on starting at 0) dimension changes. Why is that? How does the model handle this? Do you think this is already padded, or still has to be padded?

different lengt of tensor, so one is 27 handling steps, other 30. So it needs to be padded to get a good fit
