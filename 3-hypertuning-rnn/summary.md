# Report on Experiments with RNN Models for Gesture Recognition

## Objective  
The goal of this experiment was to improve the performance of an RNN model for classifying gestures. We systematically varied hyperparameters (hidden size, number of layers), RNN types (GRU vs. LSTM), and the addition of convolutional layers.

---

## Starting Point  
The baseline model (GRU, hidden size = 64, 1 layer) achieved an initial accuracy of about 48%. This is above chance level (5%, given 20 classes).

---

## Variation in Hidden Size  
- Small hidden sizes (1–16) performed poorly (3–21%).  
- 64 units achieved ~48% (default, training in a few seconds).  
- 128 units produced a significant jump to ~76%.  
- 256–512 units reached >90% (up to ~96%) but required longer training times (30–60 seconds).  
- 2048 units achieved nearly 99%, but training took ~12 minutes.  

**Conclusion:** Increasing the hidden size provides the largest improvement, but with a steep increase in computation time.

---

## Variation in Number of Layers  
- 1 layer (64 units): ~50%.  
- 3 layers (64 units): ~67% (30 sec).  
- 6 layers (64 units): no further improvement (~60%).  
- 128 hidden size, 3 layers: ~92% in 40 sec.  

**Conclusion:** Adding layers up to about 3 helps, but more layers provide no additional benefit and increase training time.

---

## GRU versus LSTM  
- Default GRU: ~51%.  
- Default LSTM: ~46%.  
- With 128 hidden size, 1 layer: LSTM ~54%, GRU ~76%.  
- With 3 layers, 128 hidden size: GRU ~91%, LSTM ~52%.  

**Conclusion:** On this dataset, GRUs clearly outperform LSTMs under comparable settings.

---

## Conv1D Layers  
- Input `(batch, time, features)` had to be transformed to `(batch, features, time)` to work with `nn.Conv1d` (e.g., 32×3×31).  
- Convolution was applied correctly and produced performance comparable to RNNs.  
- Conv1D can be useful for learning local patterns but did not outperform stronger RNN configurations in this experiment.

---

## Final Conclusion  
- The greatest performance gain came from increasing the hidden size and using 3-layer GRUs.  
- GRUs are more robust and efficient than LSTMs in this scenario.  
- Conv1D layers worked correctly but did not yield a decisive improvement.  
- With proper hyperparameters, accuracies above 90% are achievable, and even ~99% with very large models (though less efficient).
