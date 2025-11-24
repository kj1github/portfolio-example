# Summary week 4
Hypertuning fashion

1. Introduction
In de hypertuner lessen hebben we stilgestaan bij hypertunen. In het voorbeeld werden er 2 parameters gehypertuned (hidden size en num layers) op de gestures database
Dit notebook is aangepast naar de fashion dataset, waar we met een CNN model de 10 klasses proberen te voorspellen. Hierbij hebbnen we 2 paramaters die we hypertunen, te weten de learning rate en het aantal filters.
In verband met de performance van de omgeving zijn de parameters beperkt qua grootte.

2. Hypothese
   Een hoger aantal filters leid tot een hogere accuracy, maar gaat gepaard met een significate langere trainingstijd

3. Experiment
**Random search** 
   Er zijn met een 4-tal hypertuners (random search, bayes, hyperband en hyperopt) een 10-tal epochs gedraaid.
   De configuratie voor alle hypertuners is gelijk:
   * filters": tune.randint(2,16),
   * units1": 128,
   * units2": 64,
   * lr": tune.loguniform(1e-4, 3e-3)

   Hieronder de random search. 
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

**Bayes**
| Trial name         | Status      | Loc                   | Filters | LR         | Iter | Total time (s) | Valid loss | Train loss | Accuracy |
|---------------------|-------------|-----------------------|----------|-------------|------|----------------|-------------|-------------|-----------|
| tune_model_5f78883e | TERMINATED  | 192.168.3.171:116842 | 7.24356  | 0.00285707  | 10   | 122.176        | 0.467691    | 0.452028    | 0.824419  |
| tune_model_65fc9c5b | TERMINATED  | 192.168.3.171:116890 | 12.2479  | 0.00183611  | 10   | 181.936        | 0.351693    | 0.327246    | 0.871294  |
| tune_model_59367f34 | TERMINATED  | 192.168.3.171:121106 | 4.18426  | 0.000552384 | 10   | 108.299        | 0.708200    | 0.657060    | 0.737179  |
| tune_model_ece80553 | TERMINATED  | 192.168.3.171:123247 | 2.81317  | 0.00261191  | 10   | 98.127         | 2.303030    | 2.302940    | 0.099960  |
| tune_model_bece31c7 | TERMINATED  | 192.168.3.171:125326 | 10.4156  | 0.00215341  | 10   | 168.489        | 0.360762    | 0.335467    | 0.871094  |
| tune_model_545c1fb1 | TERMINATED  | 192.168.3.171:127419 | 2.28818  | 0.00291274  | 10   | 95.256         | 0.761646    | 0.755690    | 0.722556  |
| tune_model_c5ccc037 | TERMINATED  | 192.168.3.171:129657 | 13.6542  | 0.000715783 | 10   | 235.216        | 0.364605    | 0.344463    | 0.866086  |
| tune_model_338aec03 | TERMINATED  | 192.168.3.171:131654 | 4.54555  | 0.000631873 | 10   | 108.945        | 0.635046    | 0.634717    | 0.757011  |
| tune_model_2d4e9dd3 | TERMINATED  | 192.168.3.171:135802 | 6.25939  | 0.00162179  | 10   | 117.782        | 0.458425    | 0.446128    | 0.831831  |
| tune_model_ed6dac3b | TERMINATED  | 192.168.3.171:138065 | 8.04723  | 0.000944565 | 10   | 121.391        | 0.417086    | 0.411803    | 0.848858  |
| tune_model_b9db59d6 | TERMINATED  | 192.168.3.171:142308 | 2.30995  | 0.000734621 | 10   | 97.280         | 0.897623    | 0.901156    | 0.643830  |
| tune_model_9f29dd0a | TERMINATED  | 192.168.3.171:144048 | 12.1279  | 0.000879826 | 10   | 213.053        | 0.381970    | 0.352440    | 0.863882  |
| tune_model_26534897 | TERMINATED  | 192.168.3.171:146430 | 12.6878  | 0.000705197 | 10   | 186.420        | 0.371561    | 0.350321    | 0.864683  |
| tune_model_4f729bd1 | TERMINATED  | 192.168.3.171:150610 | 12.4293  | 0.00241609  | 10   | 177.635        | 0.406013    | 0.331158    | 0.844752  |
| tune_model_e159aed3 | TERMINATED  | 192.168.3.171:152808 | 12.2526  | 0.000790019 | 10   | 181.222        | 0.358030    | 0.338584    | 0.868389  |
| tune_model_ab38c71d | TERMINATED  | 192.168.3.171:157042 | 12.2481  | 0.00176234  | 10   | 232.293        | 0.372272    | 0.329483    | 0.861278  |
| tune_model_a4e28031 | TERMINATED  | 192.168.3.171:159250 | 2.00000  | 0.00300000  | 10   | 98.096         | 2.302990    | 2.303010    | 0.099760  |
| tune_model_ba91d987 | TERMINATED  | 192.168.3.171:163411 | 9.53281  | 0.001040400 | 10   | 155.628        | 0.436543    | 0.404136    | 0.842248  |


6. Analyse/reflectie
Here are the [instructions](./instructions.md) and here is a script to start [hypertune.py](./hypertune.py)

[Go back to Homepage](../README.md)
