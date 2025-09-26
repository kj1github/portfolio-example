# Excercises

- try to improve the RNN model
- default accuracy = 0,0625 (ik dacht 62,5%, maar is maar 6,2%. 20 klasses = gokkans van 5%, dus iets beter nu als een standaard gok.

- hidden size 1 = 3,5%
- hidden size = 4 = 6,5%
- hidden size = 16 = 21,5%
- hidden size = 32 = 34%
- hidden size = 64 = 47,5 = default, (10 seconds)
- hidden size = 128 = 76,5%
- hidden size = 256 = 92,8 % duurt halve minuut
- hidden size = 512 = 95,7& (duurt 1 minuut)
- hidden size = 2048 = 99% (12 minutes), that's pretty high?

hidden size = 64, layers = 1 = 50% (8 seconds)
hidden size = 64, layers = 3 = 67% (30 seconds)
hidden siez = 64, layers = 6 = 60% (24 seconds)

hidden size = 128 and layers = 3 = 92% = 40 seconds)

- test different things. What works? What does not?
Adding hidden size seems to help very well, layers 3 = good, more is not better

- experiment with either GRU or LSTM layers, create your own models. Have a look at `mltrainer.rnn_models` for inspiration.

 Default is GRU = 51%
 LSTM = 46%

 LSTM en 128 hidden size en num layers = 1  = 54%

 3 layers en 128 hidden size GRU = 51% tot 91%
 3 layers en 128 hidden size LSTM = 52%

Maakt niet heel veel uit zo op eerste gezicht, paar itteraties verder dan is GRU toch wel beter dan LSTM met zelfde settings
 
- experiment with adding Conv1D layers. Think about the necessary input-output dimensions of your tensors before and after each layer.

You should be able to get above 90% accuracy with the dataset.
Create a report of 1 a4 about your experiments.



Can you make sense of the shape?
What does it mean that the shapes are sometimes (32, 27, 3), but a second time might look like (32, 30, 3)? In other words, the second (or first, if you insist on starting at 0) dimension changes. Why is that? How does the model handle this? Do you think this is already padded, or still has to be padded?

different lengt of tensor, so one is 27 handling steps, other 30. So it needs to be padded to get a good fit
