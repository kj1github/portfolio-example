# Week 1 – Hypertuning Experiments

## Hypothesis
I expected that more epochs and larger networks (more units) would lead to higher accuracy.

---

## Experiments & Results

### Epochs
- 3 epochs: **86.2%** (1:47 min)  
- 10 epochs: **88.5%** (±6 min)  
→ More epochs help slightly but cost a lot of extra time.

### Units (units1 & units2)
- 2 units: **20%**  
- 4 units: **75%**  
- 512 units: **87%**  
- 1024 units: **86.5%** (slow)  
- 2048 units: same, no gain, even slower  

→ Too few units perform poorly, but above ~512 units there is no further improvement and only more computation time.

### Batch size
- 4: **86.7%** (10 min)  
- 32: **86.9%** (4 min)  
- 64 (default): **86.2%** (2 min)  
- 128: **87.5%** (1.5 min)  

→ Larger batch sizes train faster and sometimes even slightly better. Too small batch sizes are inefficient.

### Extra layer (deeper network)
- Standard: **87%** (1.5 min)  
- Extra dense layer: **86.6%** (2 min)  

→ No clear improvement; extra depth probably requires simultaneous tuning of other parameters.

### Learning rate / Optimizer
- Not tested due to time and setup limitations.  

![Hypertuning Result](/mnt/data/4642c8ad-8f24-476c-85a8-a2b153d9e036.png)

---

## Reflection
- **More epochs** give higher accuracy, but the gain often does not outweigh the extra computation time.  
- **Medium-sized networks (256–512 units)** are the most efficient.  
- **Increasing batch size** provides time savings and sometimes a slight quality improvement.  
- **Adding extra layers** without further tuning does not help.  
- **Hypertuning** must be done systematically: change one parameter at a time, analyze results, and learn how hyperparameters interact.

---

## Conclusion
- There is always a trade-off between model size, training time, and accuracy.  
- For this experiment, 256–512 units, larger batch sizes, and a limited number of epochs provide the best balance.  
- Combinations of hyperparameters should be further explored to find an optimal model.
