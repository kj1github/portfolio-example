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
   De configuratie voor alle hypertuners is gelijk:
   * filters": tune.randint(2,16),
   * "units1": 128,
   * "units2": 64,
   * "lr": tune.loguniform(1e-4, 3e-3)

   Hieronder de random search. Deze 
| Trial name              | Status      | Loc                  | Filters | LR          | Iter | Total time (s) | Valid loss | Train loss | Accuracy |
|--------------------------|-------------|----------------------|----------|--------------|------|----------------|-------------|-------------|-----------|
| tune_model_79a39_00000  | TERMINATED  | 192.168.3.171:62204 | 4        | 0.000309012  | 10   | 107.409        | 0.727666    | 0.731288    | 0.720453  |
| tune_model_79a39_00001  | TERMINATED  | 192.168.3.171:62203 | 14       | 0.000548393  | 10   | 245.611        | 0.384764    | 0.354075    | 0.856971  |
| tune_model_79a39_00002  | TERMINATED  | 192.168.3.171:66378 | 6        | 0.000195148  | 10   | 121.345        | 0.631182    | 0.618717    | 0.767127  |
| tune_model_79a39_00003  | TERMINATED  | 192.168.3.171:70614 | 12       | 0.000115214  | 10   | 179.696        | 0.580061    | 0.567077    | 0.777344  |
| tune_model_79a39_00004  | TERMINATED  | 192.168.3.171:70718 | 12       | 0.00122907   | 10   | 200.350        | 0.333882    | 0.317045    | 0.881010  |
| tune_model_79a39_00005  | TERMINATED  | 192.168.3.171:76905 | 7        | 0.000227039  | 10   | 123.184        | 0.557570    | 0.548583    | 0.791967  |
| tune_model_79a39_00006  | TERMINATED  | 192.168.3.171:78943 | 2        | 0.000161092  | 10   | 96.039         | 0.981258    | 0.959404    | 0.617188  |
| tune_model_79a39_00007  | TERMINATED  | 192.168.3.171:81163 | 13       | 0.000142938  | 10   | 193.846        | 0.564669    | 0.557135    | 0.789964  |
| tune_model_79a39_00008  | TERMINATED  | 192.168.3.171:81249 | 3        | 0.00127434   | 10   | 100.683        | 0.650254    | 0.643429    | 0.771034  |
| tune_model_79a39_00009  | TERMINATED  | 192.168.3.171:85391 | 13       | 0.000293134  | 10   | 197.160        | 0.477137    | 0.458287    | 0.825721  |
| tune_model_79a39_00010  | TERMINATED  | 192.168.3.171:88900 | 9        | 0.000845781  | 10   | 162.942        | 0.384921    | 0.362950    | 0.858574  |
| tune_model_79a39_00011  | TERMINATED  | 192.168.3.171:91798 | 7        | 0.00234909   | 10   | 122.680        | 0.468837    | 0.439809    | 0.829026  |
| tune_model_79a39_00012  | TERMINATED  | 192.168.3.171:93859 | 6        | 0.000134423  | 10   | 119.805        | 0.619143    | 0.602998    | 0.770132  |
| tune_model_79a39_00013  | TERMINATED  | 192.168.3.171:97904 | 2        | 0.000215996  | 10   | 97.009         | 0.907961    | 0.900510    | 0.655449  |
| tune_model_79a39_00014  | TERMINATED  | 192.168.3.171:98119 | 3        | 0.000811335  | 10   | 98.770         | 0.653565    | 0.629498    | 0.753005  |
| tune_model_79a39_00015  | TERMINATED  | 192.168.3.171:100213| 7        | 0.000300583  | 10   | 125.740        | 0.551293    | 0.536275    | 0.796775  |
| tune_model_79a39_00016  | TERMINATED  | 192.168.3.171:102306| 2        | 0.000228982  | 10   | 97.173         | 1.076780    | 1.079840    | 0.566106  |
| tune_model_79a39_00017  | TERMINATED  | 192.168.3.171:104510| 9        | 0.000230799  | 10   | 154.308        | 0.505274    | 0.490095    | 0.814002  |

<img width="927" height="405" alt="plot accuracy" src="https://github.com/user-attachments/assets/c5e59bbd-6610-43bf-b322-87cec5aa5807" />|



6. Analyse/reflectie
Here are the [instructions](./instructions.md) and here is a script to start [hypertune.py](./hypertune.py)

[Go back to Homepage](../README.md)
