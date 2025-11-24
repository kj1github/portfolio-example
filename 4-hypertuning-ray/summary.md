# Summary week 4
Hypertuning fashion

1. Introduction
In de hypertuner lessen hebben we stilgestaan bij hypertunen. In het voorbeeld werden er 2 parameters gehypertuned (hidden size en num layers) op de gestures database
Dit notebook is aangepast naar de fashion dataset, waar we met een CNN model de 10 klasses proberen te voorspellen. Hierbij hebbnen we 2 paramaters die we hypertunen, te weten de learning rate en het aantal filters.
In verband met de performance van de omgeving zijn de parameters beperkt qua grootte.

2. Hypothese
   Een hoger aantal filters leid tot een hogere accuracy, maar gaat gepaard met een significate langere trainingstijd

3. Experiment
   Er zijn met een 4-tal hypertuners (random search, bayes, hyperband en hyperopt) een 10-tal epochs gedraaid.
<img width="927" height="405" alt="plot accuracy" src="https://github.com/user-attachments/assets/c5e59bbd-6610-43bf-b322-87cec5aa5807" />




6. Analyse/reflectie
Here are the [instructions](./instructions.md) and here is a script to start [hypertune.py](./hypertune.py)

[Go back to Homepage](../README.md)
